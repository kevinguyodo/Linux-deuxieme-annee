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

Puis suffira uniquement de cliqué sur le bouton "installé", dans la colonne "Conforme CSRF", puis cliqué sur "activer".

La fenêtre qui va s'afficher devrait ressembler à l'image ci-dessous :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/Plugins.PNG)

Sur cette fenêtre on peut voir que le plugins a bien été détecté sur GLPI, et le plugin est activé.


##### Si vous souhaitez configurer le plugin, rendez-vous dans l'onget "Administration", puis "FusionInventory". Puis dans le menu horizontal vous pouvez configurer les tâches, les actions, le réseau...

### En cas du message d'alerte du cron sur GLPI, suivez les instructions suivantes :
* Dans le terminal, exécutez les commandes suivantes
  * ```sudo crontab -u www-data -e```
  * Puis sélectionnez 1 et une fenêtre apparait et frappez la commande suivante à la fin : 
  * ```*/1 * * * * /usr/bin/php5 /var/www/html/glpi/front/cron.php &>/dev/null```
  *  Et enfin on redémarre le service cron : ```/etc/init.d/cron restart```
* Sur l'interface web, allez sur le menu "Configuration" puis "Actions Automatiques"
* Et cherchez la tâches se nommant TaskScheduler, elle se trouve généralement en deuxième pages.
* Cliquez dessus et cliquez sur le bouton "Executer" comme sur la photo ci-dessous.
![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/Etape10_fusioninventory.PNG)


## Installation du logiciel FusionInventory Agent

[Lien pour télécharger FusionInventory Agent sur Windows](https://github.com/fusioninventory/fusioninventory-agent/releases)

Une fois téléchargé, vous devez éxecuter votre fichier en tant qu'administrateur.



[Retour à l'étape précédente : Création d'une GLPI](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Cr%C3%A9ation%20GLPI.md)

[Prochaine étape : Mise en place d'une sauvegarde ](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Sauvegarde%20GLPI.md)
