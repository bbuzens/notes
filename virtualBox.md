# Machine Virtuelle VirtualBox

* Penser à modifier le BIOS en activant la virtualisation pour autoriser l'utilisation de VM 64 bits
> https://www.pcastuces.com/pratique/astuces/4906.htm

* Penser à natter les IP:Ports de la machine hôtes avec les machines invitées (virtuelles)
> https://bobcares.com/blog/virtualbox-ssh-nat/

* Penser à déclarer les machines sur un réseau depuis lequel elles peuvent se voir
    * Ajouter une interface de type "réseau interne" avec un nom de réseau commun aux machines
    * Configurer l'interface éthernet sur les machines, pour CentOs :
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





