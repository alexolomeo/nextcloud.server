```yml
# Ansible Role: Nextcloud.server
# Author: Alexander Aguilar
# Email: alexolomeo@gmail.com
```

This role installs, and configures Nextcloud for Ubuntu Server 22.04, Ubuntu Server 20.04 , RHEL 8, RHEL 9

* php82
* mariadb 10.3
* Apache
* Nextcloud 

For more information, read the project wiki page: 

## Requirements

## Role Variables

| Variale Name | Required | Default Value |
| --- | --- | --- |
| `ubuntu_nextcloud_user` | yes | |
| `nextcloud_fqdn` | yes | |
| `mariadb_root_password` | yes | |
| `nextcloud_db_password` | yes | |
| `nextcloud_admin_user` | yes | |
| `nextcloud_admin_password` | yes | |


A full list of defaults and their values can be found in the `defaults/main.yml`.

## host file
```yml
[nextcloudserver]
localhost

[nextcloudserver:vars]
ansible_user=ubuntu
#ansible_become=yes
#ansible_become_method=sudo
#ansible_port= 2244
ansible_ssh_private_key_file= ./KEY-UBUNTU-JAMMY
```

## Example Playbook


```yml
---
- name: nextcloud
  hosts: nextcloudserver
  become: true

  vars:
    nextcloud_version: 26.0.3
    nextcloud_fqdn: localhost

    mariadb_root_password: XxXxX

    nextcloud_db_name: nextcloud
    nextcloud_db_user: nextcloud
    nextcloud_db_password: XxXxXx
    
    nextcloud_admin_user: admin
    nextcloud_admin_password: XxXxXdmin

    install_media: false

  roles:
    - failover.nextcloud


```

