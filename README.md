# otus-linux-hw-13-14

Scheme:
![](https://imgur.com/DAXnpvp.png)

## Vagrant file
vboxnet0 settings:
10.0.0.1/24


## Otus homework #13


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

Network interface setting are defined in **start\*.yml** files.

## Otus homework #14
Created ansible roles:
- ntp - install and run ntpd
- gauth - ssh google-auth role (link to QR in ansible output)
- top-secure - restrict access to top with pam+python script
- pam_script - install and configure pam script (restrict access to system if no internet)