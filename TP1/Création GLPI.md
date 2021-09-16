# Création GLPI

##### Avant tout de choses, veillez à bien mettre à jour votre système sur votre VM serveurs avec la commande suivante :
```
sudo apt-get update && sudo apt-get upgrade
```

##### Télécharger le plugin FusionInventory dans le bon répertoire

Il va falloir télécharger le plugin FusionInventory dans le répertoire : /usr/src. Si vous n'êtes pas dans ce répertoire, entrez la commande suivante dans le terminal :

```
cd /usr/src
```

Puis il faudra télécharger ce plugin et le décompresser. Tapez donc les deux commandes suivantes :

```
wget https://github.com/fusioninventory/fusioninventory-for-glpi/archive/glpi9.3+1.3.tar.gz
tar -zxvf glpi9.3+1.3.tar.gz -C /var/www/html/glpi/plugins
```

[Retour à l'étape précédente : Réglage réseaux](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/R%C3%A9glages%20r%C3%A9seaux.md)

[Prochaine étape : Ajout FusionInventory](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Ajout%20FusionInventory.md)
