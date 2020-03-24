# Notes Apache

## Ouverture de port firewal sur CentOS

```sh
firewall-cmd --permanent --add-service=http
firewall-cmd --reload
firewall-cmd --list-all
```