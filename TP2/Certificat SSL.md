# Certificat SSL

Pour mettre en place un certificat SSL, nous devions tout d'abord installer openssl sur notre VM. Pour rappel openssl est une bibliothèque qui permet de créer un certificat SSL gratuitement. Car il y a beaucoup de bibliothèque payante.

Pour installer openssl, on a tapé en ligne de commande :

```
sudo apt-get install openssl
```

Puis on s'est déplacé dans le dossier ssl, avec la commande :

```
cd /etc/ssl
```

Et on a créé la clé privé avec l'algorithme RSA 2048 bits avec la commande suivante :

```
openssl genrsa -out server.key 2048
```

On a donc obtenu le résultat ci-dessous :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/cr%C3%A9ation_cl%C3%A9_serveur.png)

L'étape suivante était de générer un fichier de demande de signature de certificat, on a pu faire ceci avec la commande suivante :

```
sudo openssl req -new -key server.key -out server.csr
```

Puis on a répondu à quelques questions afin de compléter la demande de signature. Le résultat obtenu était le suivant :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/demande_de_signature.png)
