# Création GLPI

##### Avant toute choses, veillez à bien mettre à jour votre système sur votre VM serveurs avec la commande suivante :
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
* Etape 9, Création base de données partie 2 : ```MariaDB [(none)]> create database glpidb; ```
* Etape 10, Création base de données partie 3 : ```MariaDB [(none)]> grant all privileges on glpidb.* to glpiuser@localhost identified by "votre-mot-de-passe";```
* Etape 11, Création base de données partie 4 : ```MariaDB [(none)]> quit ``` 
* Etape 12, Installation GLPI ligne de commande 1 : ``` cd /usr/src/```
* Etape 13, Installation GLPI ligne de commande 2 : ```wget https://github.com/glpi-project/glpi/releases/download/9.3.3/glpi-9.3.3.tgz```
* Etape 14, Installation GLPI ligne de commande 3 : ```tar -xvzf glpi-9.3.3.tgz -C /var/www/html```
* Etape 15, Attribution des droits aux servers LAMP afin d'agir sur les fichiers téléchargé précédement :  ```chown -R www-data /var/www/html/glpi/ ```

##### On va désormais configurer le GLPI via l'interface web

Afin de configurer le GLPI, on va ouvrir un moteur de recherche. Et on va tapez dans l'URL : http://adresse_ip_du_serveur/glpi.

1. Etape 1 : Choix du language

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/First_page_GLPI.PNG)

2. Etape 2 : Accepter les termes de la licence énoncés

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/seconde_page_GLPI.PNG)

3. Etape 3 : Installer le GLPI

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/3eme_page_GLPI.PNG)

4. Etape 4 : Vérifier que tous les paquets sont bien installés, puis appuyez sur continuer

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/4eme_page_GLPI.PNG)

5. Etape 5 : Création d'un utilisateur SQL

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/5eme_page_GLPI.PNG)

6. Etape 6 : Sélectionner la base de données précédement créée

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/6eme_page_GLPI.PNG)

7. Etape 7 : Appuyé sur continuer et terminer l'installation.

##### L'installation GLPI est désormais terminé


[Retour à l'étape précédente : Réglage réseaux](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/R%C3%A9glages%20r%C3%A9seaux.md)

[Prochaine étape : Ajout FusionInventory](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Ajout%20FusionInventory.md)
