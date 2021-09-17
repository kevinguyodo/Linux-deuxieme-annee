# Création sauvegarde GLPI

### Différent type de sauvegarde

* Sauvegarde Incrémental : La sauvegarde incrémentale effectue d'abord une première copie complète de toutes vos données et chaque sauvegarde qui vient après permet d'enregistrer les modifications apportées depuis la dernière sauvegarde. Cela veut dire qu'une sauvegarde initiale réalisée le 3 janvier stocke l'ensemble de vos données.
* Sauvegarde Complète : Elle consiste à copier l'ensemble des fichiers et dossiers d'un système. Chaque fois que vous effectuez une sauvegarde complète, vous stockez entièrement et une nouvelle fois la source de données.
* Sauvegarde Miroir : Une sauvegarde miroir est une copie exacte des données sources. Avec un miroir, il n’y a qu’une seule sauvegarde qui contient les fichiers de votre système tels qu’ils existaient lors de votre dernière sauvegarde
* Sauvegarde Différentielle : Une méthode de sauvegarde de données qui copie tous les fichiers qui ont été modifiés depuis le dernier backup complet. Cela inclut toutes les données qui ont été créées, mises à jour ou modifiées de quelque manière que ce soit.

### Sauvegarde créer pour GLPI

Tout va se passer dans le terminal de votre VM Linux.

Tout d'abord on va se mettre sur le compte root afin d'avoir les droits.

Puis on va se placer dans le dossier /etc/cron.daily donc pour ceci on tape la commande suivante :
```
cd /etc/cron.daily
```

Puis on va créer un fichier se nommant "backup.sh", avec ceci :
```
touch backup.sh
```

Puis on va écrire un script dedans, pour accéder au contenu du fichier on peut utiliser la commande :
```
nano backup.sh
```

Et on va donc modifier ce fichier qui est pour l'instant vide, on va introduire le script suivante :
```
#!/bin/bash
# Backup Fichier
mkdir /tmp/"backup $(date + "%d-%m-%Y %H-%M-%S")"
bkp_dir=/tmp/backup/bkp.tar.gz
glpi_dir=/var/www/html/glpi
bkp_sql=/tmp/backup/bkp.sql
bkp_gen=/tmp/backup.tar.gz
bkp=/tmp/backup

#archive des fichiers de glpi
tar -cvzf $bkp_dir $glpi_dir

#archive de la base de donnée
glpi_user=glpiuser
glpi_pass=votre_mot_de_passe_de_la_base_de_donnés
mysqldump -u$glpi_user -p$glpi_pass -h localhost DB_glpi > $bkp_sql

#archive des fichiers et de la bdd
tar -cvzf $bkp_gen $bkp
```

On va pouvoir éxecuter ce script dans le terminal avec 
```
./backup.sh
```

Ce script va donc créer une sauvegarde dans le dossier "/tmp", on va donc aller vérifier si il y a bien la présence d'une sauvegarde.
```
cd /tmp
```

Un dossier est apparu se nommant "backup date_de_la_création_du_dossier"

### Automatiser l'éxecution du script

Dans le terminal on va taper la commande :
```
crontab -e
```

Puis un

[Retour à l'étape précédente : Ajout FusionInventory](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Ajout%20FusionInventory.md)

[Prochaine étape : Messagerie](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Messagerie.md)
