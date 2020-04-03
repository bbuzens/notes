# Version Redhat/CentOS

``` bash
cat /etc/redhat-release
```

# Contrôle des processus

``` bash
ps -eaf
```

# Contrôle des file system

``` bash
df -k
du -h --max-depth=2
```

# Traces système

``` bash
strace <commande>
```
# Contrôle des ports en écoute

``` bash
netstat -tulpn | grep LISTEN
```

# Contrôle d'ouverture de port

## Avec telnet

``` bash
telnet <host> <port>
```

## Avec netcat

``` bash
nc <ip> <port>
```

## Test DNS

``` bash
nslookup <ip|host>
host <ip|host>
dig <host>
dig +noall +answer <host>
dig -x <ip>
dig +noall +answer -x <ip>
```

## Capture de trame avec tcpdump

``` bash
tcpdump -n -i en0 -w cdr.pcap
```

> Lecture possible du fichier avec Wireshark (filtre http)


# Installation CentOS

* Penser à configurer le démarrage au boot et à démarrer l'interface réseau enp0s3 après installation du système
```sh
grep ONBOOT /etc/sysconfig/network-scripts/ifcfg-enp0s3
cat /etc/sysconfig/network-scripts/ifcfg-enp0s3 | sed -e "s/ONBOOT=.*$/ONBOOT=yes/g" > /etc/sysconfig/network-scripts/ifcfg-enp0s3
ifup enp0s3
ip addr
```

* Configurer un hostname
```sh
hostname
hostnamectl set-hostname <your-new-hostname>
```
* Configurer une interface éthernet sur CentOs :
```sh
cat > /etc/sysconfig/network-scripts/ifcfg-enp0s8
TYPE=Ethernet
DEVICE=enp0s8
IPADDR=<192.168.100.101>
NETMASK=255.255.255.0
ONBOOT=yes
NOZEROCONF=yes
USERCTL=no
NM_CONTROLLED=no
<to save press ctrl-d>

ifup enp0s8
```

ou

```sh
cat << EOF > /etc/sysconfig/network-scripts/ifcfg-enp0s8
TYPE=Ethernet
DEVICE=enp0s8
IPADDR=<192.168.100.101>
NETMASK=255.255.255.0
ONBOOT=yes
NOZEROCONF=yes
USERCTL=no
NM_CONTROLLED=no
EOF
```
