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
[root@serveur1tp6 ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:6a:d1:8c brd ff:ff:ff:ff:ff:ff
    inet 10.6.202.10/24 brd 10.6.202.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe6a:d18c/64 scope link
       valid_lft forever preferred_lft forever
```
```
[root@serveur1tp6 ~]# hostname --fqdn
serveur1tp6.b1
```
* Serveur2:
```
[root@serveur2tp6 ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:08:e6:20 brd ff:ff:ff:ff:ff:ff
    inet 10.6.202.11/24 brd 10.6.202.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe08:e620/64 scope link
       valid_lft forever preferred_lft forever
```
```
[root@serveur2tp6 ~]# hostname --fqdn
serveur2tp6.b1
```
* Client1:
```
[root@client1tp6 ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:87:3f:40 brd ff:ff:ff:ff:ff:ff
    inet 10.6.201.10/24 brd 10.6.201.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe87:3f40/64 scope link
       valid_lft forever preferred_lft forever
```
```
[root@client1tp6 ~]# hostname --fqdn
client1tp6.b1
```

* Client2:
```
[root@client2 ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:3c:b9:95 brd ff:ff:ff:ff:ff:ff
    inet 10.6.201.11/24 brd 10.6.201.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe3c:b995/64 scope link
       valid_lft forever preferred_lft forever
```
```
[root@client2 ~]# hostname --fqdn
client2.tp6.b1
```
#### Check fichiers hosts
* Serveur1:
```
[root@serveur1tp6 etc]# cat hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.6.201.10 client1tp6.b1
10.6.201.11 client2tp6.b1
10.6.202.11 serveur2tp6.b1
```
* Serveur2:
```
[root@serveur2tp6 etc]# cat hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.6.201.10 client1tp6.b1
10.6.201.11 client2tp6.b1
10.6.202.10 serveur1tp6.b1
```
* Client1:
```
[root@client1tp6 etc]# cat hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.6.201.11 client2tp6.b1
10.6.202.10 serveur1tp6.b1
10.6.202.11 serveur2tp6.b1
```
* Client2:
```
[root@client2 etc]# cat hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.6.201.10 client1tp6.b1
10.6.202.10 serveur1tp6.b1
10.6.202.11 serveur2tp6.b1
```
### Configuration de OSPF
#### Pour vérifier que ça fonctionne:
* show ip ospf neigh:

Routeur1:
```
Neighbor ID     Pri   State           Dead Time   Address         Interface
4.4.4.4           1   FULL/BDR        00:00:38    10.6.100.6      Ethernet0/1
2.2.2.2           1   FULL/BDR        00:00:36    10.6.100.2      Ethernet0/0
```
Routeur2:
```
Neighbor ID     Pri   State           Dead Time   Address         Interface
3.3.3.3           1   FULL/BDR        00:00:34    10.6.100.10     Ethernet0/1
1.1.1.1           1   FULL/DR         00:00:34    10.6.100.1      Ethernet0/0
```
Routeur3:
```
Neighbor ID     Pri   State           Dead Time   Address         Interface
4.4.4.4           1   FULL/BDR        00:00:36    10.6.100.13     Ethernet0/0
2.2.2.2           1   FULL/DR         00:00:35    10.6.100.9      Ethernet0/1
5.5.5.5           1   FULL/DR         00:00:36    10.6.101.2      Ethernet0/2
```
Routeur4:
```
Neighbor ID     Pri   State           Dead Time   Address         Interface
3.3.3.3           1   FULL/DR         00:00:34    10.6.100.14     Ethernet0/0
1.1.1.1           1   FULL/DR         00:00:34    10.6.100.5      Ethernet0/1
```
Routeur5:
```
Neighbor ID     Pri   State           Dead Time   Address         Interface
3.3.3.3           1   FULL/BDR        00:00:37    10.6.101.1      Ethernet0/0
```
* traceroute:
Client1 > Serveur
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzYzNzEwNDI2LC0xNjAwODU2OTgyLC0xMj
QzOTI1NDIyLDE5NTQ3MDM3ODQsOTYzNzUwNTYyLDkwNzY4NDM4
MCw3MzA5OTgxMTZdfQ==
-->