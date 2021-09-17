# Réglages réseaux

Afin de créer une connexion entre la VM Debian(serveur) et la VM Windows(client), il nous faudra faire quelques réglages sur VMWare.

### Réglages VMWare

Pour faire quelques réglages sur la VM il faudra tout d'abord la démarrer. Une fois que votre VM est fonctionnel suivez les instructions ci-dessous.
1. En haut à droite, il y a un bouton "Player". Il vous faudra cliquer dessus.
2. Sélectionner "Manage" puis "Virtual machine settings..."
3. Une fenêtre apparaît avec tous les paramètres de votre machine, mais le paramètre qui nous intéresse, c'est celui qui se nomme "Network Adapter", il faudra donc cliquer dessus.
4. Cocher la case "Bridged" et cocher la case "Replicate physical network connection state"

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/Etape6.PNG)

#### Il faudra faire ses instructions pour les 2 machines virtuelles !

### Réglages réseaux dans les VM

#### Dans la VM serveur

Une fois dans la VM serveur, il faudra chercher son adresse ip. Il suffira d'ouvrir un terminal et de taper la commande suivante :
```
 ip addr
```

Vous trouverez donc votre Ip comme indiqué ci-dessous en rouge :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/ip.png)

#### Dans la VM Client

Après avoir constaté l'Ip de la VM serveur, nous devons vérifier l'adresse Ip de notre client. On va donc ouvrir le terminal(cmd) et taper la commande suivante :
```
ipconfig
```

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/ip_windows.PNG)

#### On voit donc que les deux VM sont dans le même réseau car il y a uniquement leurs 3 derniers chiffres qui sont différents. On peut donc passer à l'étape suivante.


[Retour à l'étape précédente : Installation des machines virtuelles](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Installation%20VM.md)

[Prochaine étape : Création d'une GLPI](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Cr%C3%A9ation%20GLPI.md)
