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
* **traceroute:**

Client1 > Serveur1
```
[root@client1tp6 etc]# traceroute serveur1tp6.b1
traceroute to serveur1tp6.b1 (10.6.202.10), 30 hops max, 60 byte packets
 1  gateway (10.6.201.254)  6.104 ms  5.896 ms  5.776 ms
 2  10.6.101.1 (10.6.101.1)  15.819 ms  15.705 ms  15.624 ms
 3  10.6.100.13 (10.6.100.13)  36.867 ms  36.748 ms  37.003 ms
 4  10.6.100.5 (10.6.100.5)  47.245 ms  47.126 ms  47.132 ms
 5  serveur1tp6.b1 (10.6.202.10)  57.814 ms !X  57.693 ms !X  57.700 ms !X
```
Client1 > Serveur2
```
[root@client1tp6 etc]# traceroute serveur2tp6.b1
traceroute to serveur2tp6.b1 (10.6.202.11), 30 hops max, 60 byte packets
 1  gateway (10.6.201.254)  10.268 ms  10.100 ms  10.097 ms
 2  10.6.101.1 (10.6.101.1)  20.217 ms  20.077 ms  20.091 ms
 3  10.6.100.13 (10.6.100.13)  30.544 ms  30.433 ms  30.419 ms
 4  10.6.100.5 (10.6.100.5)  51.529 ms  51.426 ms  51.404 ms
 5  serveur2tp6.b1 (10.6.202.11)  61.903 ms !X  61.803 ms !X  61.796 ms !X
```
Client2 > Serveur1
```
[root@client2 etc]# traceroute serveur1tp6.b1
traceroute to serveur1tp6.b1 (10.6.202.10), 30 hops max, 60 byte packets
 1  gateway (10.6.201.254)  24.338 ms  24.109 ms  24.204 ms
 2  10.6.101.1 (10.6.101.1)  45.485 ms  45.498 ms  45.709 ms
 3  10.6.100.13 (10.6.100.13)  56.607 ms  56.749 ms  67.687 ms
 4  10.6.100.5 (10.6.100.5)  78.810 ms  88.914 ms  88.995 ms
 5  serveur1tp6.b1 (10.6.202.10)  89.101 ms !X  89.188 ms !X  89.281 ms !X
```
Client2 > Serveur2
```
[root@client2 etc]# traceroute serveur2tp6.b1
traceroute to serveur2tp6.b1 (10.6.202.11), 30 hops max, 60 byte packets
 1  gateway (10.6.201.254)  5.159 ms  4.972 ms  4.919 ms
 2  10.6.101.1 (10.6.101.1)  14.966 ms  14.812 ms  14.825 ms
 3  10.6.100.13 (10.6.100.13)  25.241 ms  25.109 ms  25.137 ms
 4  10.6.100.5 (10.6.100.5)  46.321 ms  46.275 ms  46.229 ms
 5  serveur2tp6.b1 (10.6.202.11)  56.783 ms !X  56.663 ms !X  56.685 ms !X
```
Serveur1 > Client1
```
[root@serveur1tp6 etc]# traceroute client1tp6.b1
traceroute to client1tp6.b1 (10.6.201.10), 30 hops max, 60 byte packets
 1  gateway (10.6.202.254)  9.663 ms  9.462 ms  9.467 ms
 2  10.6.100.6 (10.6.100.6)  30.479 ms  30.409 ms  30.458 ms
 3  10.6.100.14 (10.6.100.14)  40.908 ms  40.796 ms  40.732 ms
 4  10.6.101.2 (10.6.101.2)  62.073 ms  61.964 ms  62.281 ms
 5  client1tp6.b1 (10.6.201.10)  72.237 ms !X  72.357 ms !X  72.232 ms !X
```
Serveur1 > Client2
```
[root@serveur1tp6 etc]# traceroute client2tp6.b1
traceroute to client2tp6.b1 (10.6.201.11), 30 hops max, 60 byte packets
 1  gateway (10.6.202.254)  8.775 ms  8.602 ms  8.645 ms
 2  10.6.100.2 (10.6.100.2)  18.808 ms  18.698 ms  18.814 ms
 3  10.6.100.10 (10.6.100.10)  39.827 ms  39.717 ms  39.654 ms
 4  10.6.101.2 (10.6.101.2)  60.805 ms  60.701 ms  60.722 ms
 5  client2tp6.b1 (10.6.201.11)  71.435 ms !X  71.327 ms !X  71.463 ms !X
```
Serveur2 > Client1
```
[root@serveur2tp6 etc]# traceroute client1tp6.b1
traceroute to client1tp6.b1 (10.6.201.10), 30 hops max, 60 byte packets
 1  gateway (10.6.202.254)  10.907 ms  10.725 ms  10.746 ms
 2  10.6.100.6 (10.6.100.6)  31.733 ms  31.610 ms  31.561 ms
 3  10.6.100.14 (10.6.100.14)  42.116 ms  42.244 ms  42.099 ms
 4  10.6.101.2 (10.6.101.2)  63.143 ms  63.045 ms  63.050 ms
 5  client1tp6.b1 (10.6.201.10)  73.615 ms !X  73.697 ms !X  73.562 ms !X
```
Serveur2 > Client2
```
[root@serveur2tp6 etc]# traceroute client2tp6.b1
traceroute to client2tp6.b1 (10.6.201.11), 30 hops max, 60 byte packets
 1  gateway (10.6.202.254)  11.008 ms  10.775 ms  10.815 ms
 2  10.6.100.2 (10.6.100.2)  31.736 ms  31.619 ms  31.550 ms
 3  10.6.100.10 (10.6.100.10)  52.712 ms  52.949 ms  52.798 ms
 4  10.6.101.2 (10.6.101.2)  58.837 ms  58.743 ms  58.865 ms
 5  client2tp6.b1 (10.6.201.11)  69.436 ms !X  69.310 ms !X  69.294 ms !X
```
Client1 > Client2
```
traceroute to client2tp6.b1 (10.6.201.11), 30 hops max, 60 byte packets
 1  client2tp6.b1 (10.6.201.11)  1.082 ms !X  1.065 ms !X  0.938 ms !X
```
Client2 > Client1
```
traceroute to client1tp6.b1 (10.6.201.10), 30 hops max, 60 byte packets
 1  client1tp6.b1 (10.6.201.10)  0.978 ms !X  0.923 ms !X  0.894 ms !X
```
Serveur1> Serveur2
```
[root@serveur1tp6 etc]# traceroute serveur2tp6.b1
traceroute to serveur2tp6.b1 (10.6.202.11), 30 hops max, 60 byte packets
 1  serveur2tp6.b1 (10.6.202.11)  2.050 ms !X  1.884 ms !X  2.176 ms !X
```
Serveur2 > Serveur1
```
[root@serveur2tp6 etc]# traceroute serveur1tp6.b1
traceroute to serveur1tp6.b1 (10.6.202.10), 30 hops max, 60 byte packets
 1  serveur1tp6.b1 (10.6.202.10)  1.011 ms !X  0.920 ms !X  0.941 ms !X
```
# Lab 3 : Let's end this properly
## 1. NAT : accès internet

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMzI0MDQ0NTQsLTI4MzM2MTQzNSwtMT
I0NjE0OTQyLC0xNjAwODU2OTgyLC0xMjQzOTI1NDIyLDE5NTQ3
MDM3ODQsOTYzNzUwNTYyLDkwNzY4NDM4MCw3MzA5OTgxMTZdfQ
==
-->