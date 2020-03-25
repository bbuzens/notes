# Notes Ansible

* Emplacement par défaut de l'inventaire

```sh
cat /etc/ansible/hosts
```

* Lancement d'une commande sur un groupe de noeuds

```sh
ansible <groupe> -a "systemctl status sshd"
```

* Lancement d'un playbook

```sh
cd poc-ansible
git pull
ansible-playbook ansible/playbook/apache_deploy.yml
```

> Initialiser le premier "fetch" avec un `git clone`

> A l'occasion, regarder le fonctionnement de la commande `ansible-pull`