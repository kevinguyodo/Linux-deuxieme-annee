# Mise en place de la Haute-Disponibilité 

### Afin de mettre en place une solution de haute-disponibilité, nous avons fait le choix d'installer corosync et pacemaker qui sont des outils nécessaire pour la mise en place de la solution.

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

Puis nous avons rajouté un dns avec l'adresse IP d'une autre VM qui sera le deuxième serveur. Comme ceci :

![]()
