# Mise en place de machine virtuelle

### Pré-requis pour l'installation d'une machine virtuelle

* Il vous faut une image iso (Windows, Linux ...) afin de simuler votre système d'exploitation
  * [Lien pour télécharger une image iso Windows](https://www.microsoft.com/fr-fr/software-download/windows10)  
  * [Lien pour télécharger une image iso Debian](https://lecrabeinfo.net/telecharger-les-iso-de-debian-11-bullseye.html)

* Une fois les deux images iso téléchargées, il nous faudra un logiciel permettant la virtualisation de poste de travail. Pour ce travail nous allons utilisé vmware workstation.
  * [Lien pour télécharger vmware workstation](https://www.vmware.com/fr/products/workstation-pro/workstation-pro-evaluation.html)

Nous avons donc tous les éléments permettant la création de deux machines virtuelles. 

### Installation de machine virtuelle

Une fois VMWare lancé, vous arrivez sur une interface graphique qui ressemble à l'image ci-dessous.

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/Pr%C3%A9sentation_VMware.PNG)

On peut voir à droite les machines virtuelles déjà créée. Et à droite on peut créer une machine virtuelle, et c'est donc cela que nous allons faire.

La première étape pour créer une machine virtuelle est de sélectionner l'image ISO téléchargée précédement. En choisissant la deuxième option proposée.

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/Etape2.PNG)

La prochaine étape est de donner un nom à votre machine virtuelle.

Ensuite nous allons attribuer un nombre de Go de mémoire à la VM, par défault VMWare propose 20Go.

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/Etape4.PNG)

Puis VMWare nous propose de voir nos paramètres que l'on a attribué à cette machine virtuelle.

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/IMG/Etape5.PNG)

Nous pouvons changer tout les paramètres en cliquant sur le bouton : "Customize Hardware...".

Puis il s'agit d'installer la machine virtuelle, pour l'installation il faudra uniquement choisir la langue, language du clavier...

### Super vous avez réussi avec succès l'installation de votre machine virtuelle, il faudra donc faire cette manipulation 2 fois afin d'avoir une machine virtuelle Windows et une machine virtuell Debian !!

[Retour au plan](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/Plan.md)

[Prochaine étape : Configuration réseau des VM](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP1/R%C3%A9glages%20r%C3%A9seaux.md)
