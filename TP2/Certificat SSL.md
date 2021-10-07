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

![]()
