# Création du site web

## Dans un premier temps nous allons créer un site internet tout simple qui affichera 'Bonjour'.

En premier lieu nous avons installé Apache2 afin de créer le serveur. Pour ce faire nous avons tapé la commande suivante dans le terminal :

```
sudo apt-get install apache2
```

Une fois apache2 installé, nous avons donc pu créer notre premier site internet. On a donc été dans le dossier html. Afin d'accéder à ce dossier nous avons tapé la commande suivante :

```
cd /var/www/html
```

Puis dans ce dossier il y a un fichier qui se nomme index.html, or nous allons le renommer en index.php. Pour renommer ce fichier nous avons tapé dans le terminal ceci :

```
mv index.html index.php
```

Puis le fichier était renommé, désormais il fallait changer le contenu de celui-ci. Pour ce faire il suffisait de taper dans le terminal :

```
nano index.php
```

Puis nous devions donner du contenu au site web, on a donc tapé les quelques lignes suivantes :

```
<?php
  echo "Bonjour";
?>
```

Puis nous avons quitté en sauvegardant, et donc notre site affichait simplement Bonjour.

### Si vous voulez tester votre site internet vous pouvez taper dans l'URL d'un moteur de recherche l'IP de votre machine, et 'Bonjour' sera affiché.

### Nous allons dès à présent attribuer à notre site un nom de domaine.

[Retour au sommaire](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/Plan.md)

[Etape 2 : Mise en place d'un nom de domaine](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/DNS.md)
