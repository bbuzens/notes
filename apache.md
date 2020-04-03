# Notes Apache

## Déclaration du service au démarrage du serveur

```sh
systemctl enable httpd
```

## Ouverture de port firewal sur CentOS

```sh
firewall-cmd --permanent --add-service=http
firewall-cmd --reload
firewall-cmd --list-all
```

# Exemples de conf apache proxy
## Conf DiagAM accès ADMIN
```
Redirect "/admin" "http://demo.diagam.sesam-vitale.fr:28080/admin/"

<Location /admin/>
    ProxyPass "http://diagam01v.gie-sv.fr:8280/"
    ProxyPassReverse "http://diagam01v.gie-sv.fr:8280/"
</Location>
```