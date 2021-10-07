# Attribution d'un nom de domaine à un site web

Tout d'abord on ne peut pas attribué le nom de domaine que l'on souhaite car beaucoup de nom de domaine sont déjà réservé. La règle pour un nom de domaine c'est le premier arrivé premier servis. Et pour réserver un nom de domaine il faut s'adresser à l'organisme gestionnaire qui en a la charge.

Pour le TP nous avons pris comme nom de domaine : www.test.elouan

Afin d'adresser un nom de domaine nous avons été dans le dossier '/etc', avec la commande suivante :

```
cd /etc
```

Puis nous avons accédé aux fichier hosts avec la commande : 
```
nano hosts
```

Une fenêtre s'est ouvert et elle ressemblait à ceci :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/fichier_hosts_sans_modification.png)

Ici on peut voir que debian et localhost sont attribué à un adresse IP, c'est pour cela que lorsqu'on tape localhost dans une barre de recherche, un site s'affiche. Or nous, nous voulions attribué un nom de domaine à notre adresse IP. Pour information il nous fallait notre adresse IP on a donc fait cette commande pour la connaître :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/IP.png)

On peut donc apercevoir que notre adresse IP était 192.168.2.129. On a donc attribué cette adresse IP à notre nom de domaine comme ci-dessous :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/change_DNS.png)

Ici on voit à droite notre adresse IP, et à gauche le nom de notre domaine.

### Il nous reste donc à tester si ça fonctionne, pour cela il faut taper dans l'URL : http://www.test.elouan

On obtient donc ce résultat :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/DNS_mis_en_place.png)

## On voit donc que tout fonctionne, la prochaine étape est la mise en place du certificat SSL

[Revenir à l'étape 1 : Création du site web](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/Cr%C3%A9ation%20site%20web.md)

[Etape 3 : Mise en place du certificat SSL](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/Certificat%20SSL.md)
