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

### On a voulu vérifier les informations entrées, on a donc tapé la commande suivante :

```
sudo openssl req -text -noout -in server.csr
```

On a donc ceci en retour : 

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/verification_donn%C3%A9es.png)

#### On voit donc que toute nos information qui ont été entré sont valides

La prochaine étape est l'auto-signature du certificat, pour cela on a entré la commande suivante :

```
sudo openssl x509 -req -days 365 -in server.csr -signkey server.key server.crt
```

Cette commande va permettre de créer le certificat SSL valide pendant 365 jours et au format x509

On obtient donc le résultat suivant :

![](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/IMG/ssl_signature.png)

#### Il reste une dernière étape.

La dernière étape était de changer deux lignes dans le fichier default-ssl.conf, qui se trouve dans le fichier ssl.

Pour accéder à ce fichier on a tapé la commande suivante :

```
nano /etc/ssl/default-ssl.conf
```

Une fois dans le fichier, il faudra s'assurer que les deux lignes : 'SSLCertificateFile' et 'SSLCertificateKeyFile' ont pour valeur, '/etc/ssl/server.crt' et '/etc/ssl/server.key'. Comme sur l'exemple ci-dessous :

![]()

### On a donc créé le certificat SSL valide pendant 1 an, la prochaine et dernière étape est la mise en place d'une solution haute-disponibilité.

[Retour à l'étape précédente : Attribution nom de domaine](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/DNS.md)

[Etape 4 : Mise en place d'une solution de haute-disponibilité](https://github.com/kevinguyodo/Linux-deuxieme-annee/blob/main/TP2/Haute%20disponibilit%C3%A9.md)
