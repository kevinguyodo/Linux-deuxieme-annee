# Mise en place de la Haute-Disponibilité 


### Schéma représentant une solution simple de la Haute-disponibilité :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/sch%C3%A9ma_haute-disponibilit%C3%A9.png)


### Afin de mettre en place une solution de haute-disponibilité, nous avons fait le choix d'installer corosync et pacemaker qui sont des outils nécessaires pour la mise en place de la solution.

On a donc installé corosync et pacemaker dans le terminal avec la ligne de commande suivante :

```
sudo apt-get install corosync pacemaker crmsh
```

crmsh est le terminal de pacemaker.


### Une fois les outils nécessaires installés, nous avons configuré le cluster HA(regroupement d'ordinateur qui prennent en charge les applications serveurs).

Tout d'abord on a rajouté un serveur dans le fichier /etc/hosts. Pour ce faire nous avons tapé la commande suivante :

```
sudo nano /etc/hosts
```

Puis nous avons rajouté un DNS avec l'adresse IP d'une autre VM qui sera le deuxième serveur. Comme ceci :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/rajout_d'un_serveur.png)

On peut donc voir qu'on a rajouté un serveur avec l'adresse IP suivante : 192.168.2.130, qui a comme nom de domaine www.test2.elouan

#### On avait donc 2 serveurs avec deux adresses IP différente :
#### * Premier serveur avec une adresse IP = 192.168.2.129
#### * Deuxième serveur avec une adresse IP = 192.168.2.130

L'étape suivante était pour nous d'ouvrir  les port UDP 5404 et 5405 en entrée et sortie, avec la commande suivante :
 ```
sudo iptables -I INPUT -m state --state NEW -p udp -m multiport --dports 5404,5405 -j ACCEPT
sudo iptables -I OUTPUT -m state --state NEW -p udp -m multiport --sports 5404,5405 -j ACCEPT
 ```
 
 Puis nous avons généré la clé d'authentification pour la communication de corosync entre les deux serveurs comme ceci :
 
 ```
 sudo corosync-keygen
 ```
 
 ![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/corosync-leygen.png)
 
 ##### On voit donc ici que la clé a bien été créée correctement
 
 Puis les prochaines étapes était de faire des copies de fichiers d'un serveur à un autre. Nous allons donc voir ça ensemble point par point :
 
 #### 1. Dans un premier temps nous devions copier le fichier authkey vers le nouveau serveur, pour ce faire nous avons été sur la deuxième VM qui possède le role de deuxième serveur et nous avons suivis le schéma suivant :
 ```
 sudo scp nom_utilisateur@adresse_ip_serveur1 chemin_du_fichier_dans_le_serveur1 emplacement_voulu_dans_le_server2
 ```
 
 Ceci nous donne le résultat suivant :
 
 ![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/copie_fichier1.png)
 
 La première copie a bien été effecuté
 
 #### 2. De retour dans l'ordinateur ayant comme fonction le premier serveur, on a créé la nouvelle configuration de corosync, on est donc rentré dans le fichier corosync.conf avec la commande suivante :
 
 ```
 nano /etc/corosync/corosync.conf
 ```
 
 Puis on a tapé la configuration suivante :
 
 ```
 logging {
  debug: off
  to_syslog: yes
}
nodelist {
  node {
    name: www.test.elouan
    nodeid: 1
    quorum_votes: 1
    ring0_addr: 192.168.2.129
  }
  node {
    name: www.test2.elouan
    nodeid: 2
    quorum_votes: 1
    ring0_addr: 192.168.2.130
  }
}
quorum {
  provider: corosync_votequorum
}
totem {
  cluster_name: cluster-ha
  config_version: 3
  ip_version: ipv4
  secauth: on
  version: 2
  
  interface {
    bindnetaddr: 192.168.2.129
    ringnumber: 0
  }
}
 ```
 
 Donc dans cette configuration on va définir que le premier serveur utilisé sera www.test.elouan et le second serveur utilisé en cas de panne ou autre problème technique  sera www.test2.elouan
 
 
 #### 3. On a donc fait le copie de cette configuration dans l'ordinateur du serveur 2, on a repris le même schéma expliqué au dessus, ce qui nous donne l'exemple suivant :
 
 ![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/Copie_configuration.png)
 
 La copie a donc bien été effectué
 
 #### C'était la fin des copies d'un serveur à l'autre, les étapes suivantes était pour nous de démarrer les services corosync et pacemaker 
 
 Pour ce faire nous avons entré deux commande dans le terminal : 
 
 ```
systemctl start corosync
systemctl start pacemaker
 ```
 
 Puis nous avons vérifié l'état du cluster avec la commande suivante :
 
 ```
 sudo crm status
 ```
 
 Le résultat que nous avons obtenu est celui-ci :
 
 ![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/crm_status.png)
 
 #### La prochaine étape était de lier les deux serveur sur un même serveur afin de faire fonctionner le site web correctement.
 
 L'adresse IP de notre serveur sera : 192.168.2.131
 
 On a onc relié nos serveur créer précèdement à notre serveur qui hébergera le site web.
 
 On a modifié le fichier interfaces qui se trouve dans le dossier /etc/network. Pour ce faire on a tapé la commande suivante :
 
 ```
 nano /etc/network/interfaces
 ```
 
 Puis en bas du fichier on a tapé la configuration suivante :
 
 ```
 auto ens33:1
 iface ens33:1 inet static
   address 192.168.2.131
   netmask 255.255.255.0
 ```
 
 Puis on va restart le service network. Avec la commande :

```
systemctl restart networking
```
 
 Et l'étape suivante était de créer une adresse IP virtuelle, donc c'est l'adresse IP de notre serveur web, donc 192.168.2.131
 
 Pour ce faire on a tapé la commande suivante :
 
 ```
 sudo crm configure primitive VIP ocf:heartbeat:IPaddr2 params ip="192.168.2.131" cidr_netmask="24" nic="ens33:1" op monitor interval="10s" timeout="20" meta failure-timeout="5"
 ```
 Puis on créer un groupe de ressources avec l'IP virtuelles configurer précédement, on fait ceci avec la commande suivante :
 
 ```
 sudo crm configure location grpipv grpipv-location grpipv 50: www.test.elouan
 ```
 
 On va ensuite checker le status de notre cluster afin de voir si il est bien fonctionnel, avec :
 
```
sudo crm status
```

Et on obtient le résultat suivant, qui nous montre que notre cluster est bien fonctionnel.

![]()
 ### On a donc réussi à créer une solution de haute disponibilité, la solution que l'on a créée ressemble au schéma se trouvant tout en haut  
 
 [Retour à l'étape précédente : Certificat SSL](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/Certificat%20SSL.md)
 
 [Conclusion](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/Conclusion.md)
 
