# FusionInventory

##### Télécharger le plugin FusionInventory dans le bon répertoire

Il va falloir télécharger le plugin FusionInventory dans le répertoire : /usr/src. Si vous n'êtes pas dans ce répertoire, entrez la commande suivante dans le terminal :

```
cd /usr/src
```

Puis il faudra télécharger ce plugin et le décompresser. Tapez donc les deux commandes suivantes :

```
sudo wget https://github.com/fusioninventory/fusioninventory-for-glpi/archive/glpi9.3+1.3.tar.gz
sudo tar -zxvf glpi9.3+1.3.tar.gz -C /var/www/html/glpi/plugins
```

On va ensuite donner les droits d'accès au serveur web afin qu'il puisse l'utiliser, la commande qui fera ceci est :

```
sudo chown -R www-data /var/www/html/glpi/plugins
```

Afin de rendre visible le plugins dans le GLPI, il y a deux commandes à entrer : 

```
cd /var/www/html/glpi/plugins
mv fusioninventory-for-glpi-glpi9.3-1.3/ fusioninventory/
```

##### Sur l'interface web

Désormais nous allons sur l'interface web, donc dans l'URL nous allons taper : adresse_ip_serveur/glpi.

Puis dans le menu horizontal, nous allons cliquer sur Configuration puis Plugins.

La fenêtre qui va s'afficher devrait ressembler à l'image ci-dessous :

![]()

[Retour à l'étape précédente : Création d'une GLPI](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Cr%C3%A9ation%20GLPI.md)

[Prochaine étape : Mise en place d'une sauvegarde ](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Sauvegarde%20GLPI.md)
