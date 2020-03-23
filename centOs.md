# Installation CentOS

* Penser à configurer le démarrage au boot et à démarrer l'interface réseau enp0s3 après installation du système
```sh
grep ONBOOT /etc/sysconfig/network-scripts/ifcfg-enp0s3
cat /etc/sysconfig/network-scripts/ifcfg-enp0s3 | sed -e "s/ONBOOT=.*$/ONBOOT=yes/g" > /etc/sysconfig/network-scripts/ifcfg-enp0s3
ifup enp0s3
ip addr
```