# B1 Réseau 2018 - TP6
# Lab 2 : Un peu de complexité (et d'utilité ?...)
## 2. Mise en place du lab
### Checklist IP Routeurs + Nom de domaine
* Routeur1:
```
r1.tp6.b1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.6.100.1      YES NVRAM  up                    up
Ethernet0/1                10.6.100.5      YES NVRAM  up                    up
Ethernet0/2                10.6.202.254    YES NVRAM  up                    up
Ethernet0/3                unassigned      YES NVRAM  administratively down down
```
* Routeur2:
```
r2.tp6.b1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.6.100.2      YES NVRAM  up                    up
Ethernet0/1                10.6.100.9      YES NVRAM  up                    up
Ethernet0/2                unassigned      YES NVRAM  administratively down down
Ethernet0/3                unassigned      YES NVRAM  administratively down down
```
* Routeur3:
```
r3.tp6.b1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.6.100.14     YES NVRAM  up                    up
Ethernet0/1                10.6.100.10     YES NVRAM  up                    up
Ethernet0/2                10.6.101.1      YES NVRAM  up                    up
Ethernet0/3                unassigned      YES NVRAM  administratively down down
```
* Routeur4:
```
r4.tp6.b1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.6.100.13     YES NVRAM  up                    up
Ethernet0/1                10.6.100.6      YES NVRAM  up                    up
Ethernet0/2                unassigned      YES NVRAM  administratively down down
Ethernet0/3                unassigned      YES NVRAM  administratively down down
```
* Routeur5:
```
r5.tp6.b1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.6.101.2      YES NVRAM  up                    up
Ethernet0/1                10.6.201.254    YES NVRAM  up                    up
Ethernet0/2                unassigned      YES NVRAM  administratively down down
Ethernet0/3                unassigned      YES NVRAM  administratively down down
```
### Checklist VMs
* Serveur1:
```

```
* Serveur2:
```

```
* Client1:
```

```
* Client2:
```

```
### Vérifier que tout ça fonctionne
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTYzNzUwNTYyLDkwNzY4NDM4MCw3MzA5OT
gxMTZdfQ==
-->