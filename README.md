# my-pki-with-libellum
----------------------

Installation d'une PKI avec le projet Libellum
https://github.com/Eternilab/step-ca

## Utilisation

- Copier et modifier hosts.yml.exemple -> hosts.yml
- Copier et modifier groupvars/debian.exemple -> groupvars/debian

## Exemple d'inventaire

all:
  children:
    debian:
      hosts:
        ra.my-domain.com:
          ansible_host: 10.14.5.52
          ansible_hostname: ra
          ipv4: 10.14.5.52
        va.my-domain.com:
          ansible_host: 10.14.5.53
          ansible_hostname: va
          ipv4: 10.14.5.53
        ca.my-domain.com:
          ansible_host: 10.14.5.54
          ansible_hostname: ca
          ipv4: 10.14.5.54
        # Ansible controller
        admin.my-domain.com:
          ansible_host: 10.14.5.55
          #ansible_hostname: admin
          ipv4: 10.14.5.55
    ca_server:
      hosts:
        ca.my-domain.com:
    ra_servers:
      hosts:
        ra.my-domain.com:
    va_servers:
      hosts:
        va.my-domain.com:


## Commandes 

### Update paquets debian

``` ansible-playbook playbooks/update.yml ```

### Upgrade debian

``` ansible-playbook playbooks/upgrade.yml ```

### Lancement playbook

``` ansible-playbook site.yml ```

### Durcissement hotes

``` ansible-playbook site.yml -t hardenning ```

### Telechargement des roles

``` ansible-galaxy install -r requirements.yml -v --keep-scm-meta ```

# LICENCE
---------

MIT

# AUTEUR
--------

Benoit Nivesse
benoit@nivesse.com
