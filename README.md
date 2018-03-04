# otus-linux-hw

Scheme:
![](https://raw.githubusercontent.com/fl64/otus-linux-hw/master/draw.io-scheme.png)

## Vagrant file
vboxnet0 settings:
10.0.0.1/24


## Otus homework #13 Networking

Created ansible roles:
- bird - install and configure bird
- common - add EPEL repo, install bird, quagga
- dummy - enable mod dummy
- edgefw - install and confgure edge firewall (r0)
- forward - enable ip_forward
- named - install and configure named master and slaves 
- networking - create and configure vlan and dummies
- quagga - install and confugure quagga
- openbfdd - download, compile, install and configure openbfdd

Network interface settings are defined in **start\*.yml** files.

## Otus homework #14 PAM

Created ansible roles:
- ntp - install and run ntpd
- gauth - ssh google-auth role (link to QR in ansible output)
- top-secure - restrict access to top with pam+python script
- pam_script - install and configure pam script (restrict access to system if no internet)

## Otus homework #15 LDAP

Created ansible roles:
- dns_resolver - install lab dns-server as dns resolver
- openldap-client - deploy LDAP auth 
- openldap-server - deploy LDAP server

**LDIFs files:**

* [Deploy Main settings + Auth](https://github.com/fl64/otus-linux-hw/tree/master/roles/openldap-server/templates/1_init.j2)
* [Deploy restrictions](https://github.com/fl64/otus-linux-hw/tree/master/roles/openldap-server/templates/2_monitor.j2)
* [Deploy SSL\TLS-security](https://github.com/fl64/otus-linux-hw/tree/master/roles/openldap-server/templates/3_tls.j2)
* [LDAP Structure (autogenerated with 4_ldap_struct.j2)](https://github.com/fl64/otus-linux-hw/tree/master/roles/openldap-server/templates/ldapstruct.ldif.j2)

Autiomation for LDAP Struct: https://github.com/fl64/otus-linux-hw/blob/master/roles/openldap-server/templates/4_ldap_struct.j2


## Otus homework #16 Backup

Created ansible roles:
- openldap-backup - deploy bash script to backup LDAP.
- bacula-dir - install and configure Bacula Director
- bacula-sd - install and configure Bacula Storage Director
- bacula-fd - install and configure File Daemon

Playbook to run: **hw16_backups.yaml**

Command to run: `ansible-playbook -i inventory hw16_backups.yaml --ask-vault-pass`

## Otus homework #17 Monitoring

Created roles: 
- zabbix-server
- zabbix-agent
- mariadb
- graphite

Playbook to run: **hw17_graphite.yaml**

Zabbix templates: [zbx_export_templates.xml](https://raw.githubusercontent.com/fl64/otus-linux-hw/master/zbx_export_templates.xml)

## Otus homework #18 Apache + Nginx

Created role: 
- hw-apache-nginx

Playbook to run: **hw18_apache_nginx.yaml**

Configs: 
* [Apache](https://github.com/fl64/otus-linux-hw/tree/master/roles/hw-apache-nginx/templates/sites_apache.conf.j2)
* [Nginx](https://github.com/fl64/otus-linux-hw/tree/master/roles/hw-apache-nginx/templates/sites_nginx.conf.j2)

### Optional task:
SSL +  Basic CGI Scripts (sh,py)

Created role: 
- apache-nginx

Playbook to run: **same**