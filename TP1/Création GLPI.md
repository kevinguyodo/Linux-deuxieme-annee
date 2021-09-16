# Création GLPI

##### Avant tout de choses, veillez à bien mettre à jour votre système sur votre VM serveurs avec la commande suivante :
```
sudo apt-get update && sudo apt-get upgrade
```

##### Pour la création GLPI, ça va être beaucoup de commande dans le terminal linux

Donc dans le terminal linux, nous allons installer beaucoup d'outils afin de travailler avec GLPI. Les commandes suivantes sont à rentrer dans le terminal.

* Etape 1, Installer Apache2 : ``` sudo apt-get install apache2 php libapache2-mod-php ```
* Etape 2, Installer PHP : ```sudo apt-get install php-imap php-ldap php-curl php-xmlrpc php-gd php-mysql php-cas ```
* Etape 3, Installer MariaDB partie 1 : ```sudo apt-get install mariadb-server```
* Etape 4, Installer MariaDB partie 2 : ```mysql_secure_installation```
* Etape 5, Installer modules complémentaires : ```sudo apt-get install apcupsd php-apcu```
* Etape 6, Redémarrage service Apache2 : ```/etc/init.d/apache2 restart```
* Etape 7, Redémarrage service MySQL : ```/etc/init.d/mysql restart```
* Etape 8, Création d'une base de données : ```mysql -u root -p```
* Etape 9, Création base de données partie2 : \```MariaDB [(none)]> create database glpidb; 
MariaDB [(none)]> grant all privileges on glpidb.* to glpiuser@localhost identified by "votre-mot-de-passe";
MariaDB [(none)]> quit ```
* Etape 10



[Retour à l'étape précédente : Réglage réseaux](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/R%C3%A9glages%20r%C3%A9seaux.md)

[Prochaine étape : Ajout FusionInventory](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Ajout%20FusionInventory.md)
