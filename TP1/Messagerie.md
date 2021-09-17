## Messagerie

##### Pour créer un système de messagerie on va aller sur l'interface web GLPI. 

Tout d'abord il faut se connecter à la GLPI, puis aller dans le menu "Configuration" -> Authentification -> Serveurs de messagerie.

Puis dans le menu horizontal, cliqué sur "+", afin d'ajouter une messagerie.

Une fenêtre ressemblant à ceci devrait apparaitre :
![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/Messagerie_1.PNG)

Il suffit donc de remplir les champs, mais nous allons expliquer chaque champ :
1. Premier champ : C'est le nom du serveur qui sera affiché dans GLPI
2. Deuxième champ : C'est le domaine de messagerie, ceci correspond à ce qui va suivre l'arobase, exemple type de messagerie : nom.prenom@nom_domaine_de_messagerie.fr, or ici il faut uniquement mettre le nom du domaine de messagerie
3. Troisième champ : Le nom pleinement qualifié du serveur, exemple : imap.nom_du_domaine_de_messagerie.com
4. Quatrième champ : C'est les paramètres optionnel de connexion au serveur, donc il faudra choisir les paramètres suivante : IMAP, SSL, TLS, NO-VALIDATE-CERT
5. Cinquième champ : Choisir le dossier des messages entrants, par défault il faut mettre INBOX.

Un exemple avec le champs rempli :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/Messagerie_2.PNG)

Puis valider la messagerie, et lors de la validation en bas à droite il y a une pop-up qui apparait on va donc cliqué dessus et on verra donc que la messagerie est bien fonctionnel.

##### Vous avez réussi à créer votre messagerie !!

[Retour à l'étape précédente : Sauvegarde GLPI](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Sauvegarde%20GLPI.md)

[Conclusion](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Conclusion.md)
