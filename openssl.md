## SSL

### Conversiont de PEM vers P12

```bash
openssl pkcs12 -in path.p12 -out newfile.crt.pem -clcerts -nokeys
openssl pkcs12 -in path.p12 -out newfile.key.pem -nocerts -nodes
```

réciproquement:
```bash
openssl pkcs12 -export -descert -in $1.crt -inkey $1.key -passin pass:integ -passout pass:integ -name $1 -caname $1 -out $1.p12
```

### Contrôle de certificat

#### Contrôle de connexion à un service SSL existant

``` bash
openssl s_client -connect demo.diagam.sesam-vitale.fr:28443 -showcerts -servername demo.diagam.sesam-vitale.fr
```

#### Contrôle d'une chaîne de certification générée chez nous

Monter un serveur OpenSSL

``` bash
openssl s_server -key key.pem -cert cert.pem -accept 44330 -www -CAfile cas.bundle -verify 10
```

> Voir avec David les clés/certificat utilisés et la consitution d'un CAfile

Contrôler la connexion SSL au serveur

``` bash
openssl s_client -connect localhost:44330 -showcerts -cert ../CPS001.crt -key ../CPS001.key -pass pass:integ
```

Contrôler la validité du P12 à l'aide d'un navigateur

``` bash
curl --cert-type P12 --cert cert.p12:password https://localhost:44330
```

#### Afficher un certificat (données entre BEGIN CERTIFICATE et END CERTIFICATE de la commande précédente)

``` bash
openssl x509 -in /tmp/t.crt -noout -text
```

Ou pour afficher plein de certificats en appliquant un filtre sur les données en sortie
``` bash
ls AC*.crt | xargs -I % sh -c 'openssl x509 -in % -text -noout' | grep "Subject:"
```

#### Afficher un fichier de demande de certificat (csr)

``` bash
openssl req -text -noout -verify -in CDET001.csr
```

### Supprimer un passaphrase sur une clé

``` bash
openssl rsa -in [file1.key] -out [file2.key]
```

## JKS

### Import de certificat dans un JKS

``` bash
keytool -importkeystore -destkeystore keystore.jks -srckeystore CPET0001.p12 -srcstoretype pkcs12 -alias CPET0001 -destkeypass integration
keytool -list -keystore keystore.jks
```

### Export de certificat depuis un JKS
```bash
keytool -export -alias foo -file certfile.cer -keystore privateKey.store
```