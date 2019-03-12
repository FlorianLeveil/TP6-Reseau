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


# Requête web vers un site full HTTP, avec résolution de nom
* Utilisation de la commande: `telnet trip-hop.net 80 GET /`:
```
r4.tp6.b1#telnet trip-hop.net 80
Trying trip-hop.net (213.186.33.4, 80)... Open
GET/
HTTP/1.1 400 Bad Request
Server: squid
Mime-Version: 1.0
Date: Tue, 12 Mar 2019 10:31:22 GMT
Content-Type: text/html;charset=utf-8
Content-Length: 4104
X-Squid-Error: ERR_INVALID_REQ 0
Vary: Accept-Language
Content-Language: fr
X-Cache: MISS from PF1-BOR1FR
X-Cache-Lookup: NONE from PF1-BOR1FR:3128
Connection: close


<html><head>
            <meta type="copyright" content="Copyright (C) 1996-2017 The Squid Software Foundation and contributors">
                                         <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
                                 <title>ERREUR : l'URL demandée n'a pas pu être chargée</title>
                    <style type="text/css"><!--
                                                 /*
                                                    * Copyright (C) 1996-2017 The Squid Software Foundation and contributors
                                                  *
                                                    * Squid software is distributed under GPLv2+ license and includes
                                           * contributions from numerous individuals and organizations.
                             * Please see the COPYING and CONTRIBUTORS files for details.
               */

                 /*
                    Stylesheet for Squid Error pages
                                                     Adapted from design by Free CSS Templates
                    http://www.freecsstemplates.org
                                                    Released for free under a Creative Commons Attribution 2.5 License
                                           */

                                             /* Page basics */
                                                              * {
                                                                        font-family: verdana, sans-serif;
                              }

                               html body {
                                                margin: 0;
                                                                padding: 0;
                                                                          background: #efefef;
                        font-size: 12px;
                                                color: #1e1e1e;
                                                               }

                                                                /* Page displayed title area */
                    #titles {
                                margin-left: 15px;
                                                        padding: 10px;
                                                                        padding-left: 100px;
                        background: url('/squid-internal-static/icons/SN.png') no-repeat left;
                   }

                    /* initial title */
                                       #titles h1 {
                                                        color: #000000;
                                                                       }
                                                                        #titles h2 {
                color: #000000;
                               }

                                /* special event: FTP success page titles */
 #titles ftpsuccess {
                        background-color:#00ff00;
                                                        width:100%;
                                                                   }

                                                                    /* Page displayed body content area */
                               #content {
                                                padding: 10px;
                                                                background: #ffffff;
         }

          /* General text */
                            p {
                               }

                                /* error brief description */
                                                             #error p {
                                                                       }

                                                                        /* some data which may have caused the problem */
                                              #data {
                                                     }

                                                      /* the error message received from the system or other software */
                                             #sysmsg {
                                                      }

                                                       pre {
                                                                font-family:sans-serif;
            }

             /* special event: FTP / Gopher directory listing */
                                                                #dirmsg {
                                                                             font-family: courier;
                           color: black;
                                            font-size: 10pt;
                                                            }
                                                             #dirlisting {
                                                                              margin-left: 2%;
                       margin-right: 2%;
                                        }
                                         #dirlisting tr.entry td.icon,td.filename,td.size,td.date {
                            border-bottom: groove;
                                                  }
                                                   #dirlisting td.size {
                                                                            width: 50px;
                 text-align: right;
                                       padding-right: 5px;
                                                          }

                                                           /* horizontal lines */
      hr {
                margin: 0;
                          }

                           /* page displayed footer area */
                                                           #footer {
                                                                        font-size: 9px;
                padding-left: 10px;
                                   }


                                    body
                                        :lang(fa) { direction: rtl; font-size: 100%; font-family: Tahoma, Roya, sans-serif; float: right; }
                                                                :lang(he) { direction: rtl; }
                   --></style>
                              </head><body id="ERR_INVALID_REQ">
                                                                <div id="titles">
      <h1>ERREUR</h1>
                     <h2>L'URL demandée n'a pas pu être trouvé</h2>
                                                                   </div>
                                                                         <hr>

  <div id="content">
                    <p><b>Requête invalide</b> une erreur a été rencontrée en essayant de traiter la requête :</p>

                                       <blockquote id="data">
                                                             <pre>GET/
</pre>
      </blockquote>

                   <p>Problèmes possibles :</p>
                                               <ul>
                                                   <li id="missing-method"><p>Requête de la méthode non précisée ou inconnue.</p></li>
                                                           <li id="missing-url"><p>L'URL n'est pas spécifiée</p></li>
                                          <li id="missing-protocol"><p>L'identifiant HTTP est absent pour (HTTP/1.0).</p></li>
                                                   <li><p>La requête est trop grande</p></li>
                  <li><p>Le champ "Content-Length" est absent, pour l'utilisation des requêtes avec POST ou PUT</p></li>
                                             <li><p>Caractère illégal dans le nom d'hôte; Le caractère tiret bas n'est pas autorisé.</p></li>
                                                                  <li><p>HTTP/1.1 <q>Expect:</q> cette fonction a besoin du logiciel HTTP/1.0.</p></li>
 </ul>

      <p>Votre administrateur proxy est <a href="mailto:support@ynov-bordeaux.com?subject=CacheErrorInfo%20-%20ERR_INVALID_REQ&amp;body=CacheHost%3A%20PF1-BOR1FR%0D%0AErrPage%3A%20ERR_INVALID_REQ%0D%0AErr%3A%20%5Bnone%5D%0D%0ATimeStamp%3A%20Tue,%2012%20Mar%202019%2010%3A31%3A22%20GMT%0D%0A%0D%0AClientIP%3A%2010.33.1.153%0D%0A%0D%0AHTTP%20Request%3A%0D%0A%0D%0A%0D%0A">support@ynov-bordeaux.com</a>.</p>
                             <br>
                                 </div>

                                       <script language="javascript">
                                                                     if ('[unknown method]' != '[unknown method]') document.getElementById('missing-method').style.display = 'none';
                              if ('error:invalid-request' != '[no URL]') document.getElementById('missing-url').style.display = 'none';
                                                            if ('[unknown protocol]' != '[unknown protocol]') document.getElementById('missing-protocol').style.display = 'none';
                           </script>

                                    <hr>
                                        <div id="footer">
                                                         <p>Générée le Tue, 12 Mar 2019 10:31:22 GMT par PF1-BOR1FR (squid)</p>
                                                    <!-- ERR_INVALID_REQ -->
 </div>
       </body></html>

[Connection to trip-hop.net closed by foreign host]
```
**Efectivement il y a beaucoup HTML !!!**
* Vérification des passerelles par défaut des routeurs:

Routeur1:
```
r1.tp6.b1#show ip route
Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route

Gateway of last resort is 10.6.100.6 to network 0.0.0.0

     10.0.0.0/8 is variably subnetted, 7 subnets, 2 masks
O       10.6.100.8/30 [110/20] via 10.6.100.2, 00:24:32, Ethernet0/0
O       10.6.100.12/30 [110/20] via 10.6.100.6, 00:24:32, Ethernet0/1
C       10.6.100.0/30 is directly connected, Ethernet0/0
O IA    10.6.101.0/30 [110/30] via 10.6.100.6, 00:24:32, Ethernet0/1
                      [110/30] via 10.6.100.2, 00:24:32, Ethernet0/0
C       10.6.100.4/30 is directly connected, Ethernet0/1
O IA    10.6.201.0/24 [110/40] via 10.6.100.6, 00:24:34, Ethernet0/1
                      [110/40] via 10.6.100.2, 00:24:34, Ethernet0/0
C       10.6.202.0/24 is directly connected, Ethernet0/2
O*E2 0.0.0.0/0 [110/1] via 10.6.100.6, 00:24:34, Ethernet0/1

```
Routeur2:
```
r2.tp6.b1#show ip route
Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route

Gateway of last resort is 10.6.100.10 to network 0.0.0.0

     10.0.0.0/8 is variably subnetted, 7 subnets, 2 masks
C       10.6.100.8/30 is directly connected, Ethernet0/1
O       10.6.100.12/30 [110/20] via 10.6.100.10, 00:24:32, Ethernet0/1
C       10.6.100.0/30 is directly connected, Ethernet0/0
O IA    10.6.101.0/30 [110/20] via 10.6.100.10, 00:24:32, Ethernet0/1
O       10.6.100.4/30 [110/20] via 10.6.100.1, 00:24:32, Ethernet0/0
O IA    10.6.201.0/24 [110/30] via 10.6.100.10, 00:24:32, Ethernet0/1
O IA    10.6.202.0/24 [110/20] via 10.6.100.1, 00:24:33, Ethernet0/0
O*E2 0.0.0.0/0 [110/1] via 10.6.100.10, 00:24:33, Ethernet0/1
               [110/1] via 10.6.100.1, 00:24:33, Ethernet0/0

```
Routeur3:
```
r3.tp6.b1#show ip route
Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route

Gateway of last resort is 10.6.100.13 to network 0.0.0.0

     10.0.0.0/8 is variably subnetted, 7 subnets, 2 masks
C       10.6.100.8/30 is directly connected, Ethernet0/1
C       10.6.100.12/30 is directly connected, Ethernet0/0
O       10.6.100.0/30 [110/20] via 10.6.100.9, 00:24:31, Ethernet0/1
C       10.6.101.0/30 is directly connected, Ethernet0/2
O       10.6.100.4/30 [110/20] via 10.6.100.13, 00:24:31, Ethernet0/0
O       10.6.201.0/24 [110/20] via 10.6.101.2, 01:01:28, Ethernet0/2
O IA    10.6.202.0/24 [110/30] via 10.6.100.13, 00:24:32, Ethernet0/0
                      [110/30] via 10.6.100.9, 00:24:32, Ethernet0/1
O*E2 0.0.0.0/0 [110/1] via 10.6.100.13, 00:24:32, Ethernet0/0

```
Routeur4:
```
r4.tp6.b1#show ip route
Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route

Gateway of last resort is 192.168.122.1 to network 0.0.0.0

C    192.168.122.0/24 is directly connected, Ethernet0/2
     10.0.0.0/8 is variably subnetted, 7 subnets, 2 masks
O       10.6.100.8/30 [110/20] via 10.6.100.14, 00:24:30, Ethernet0/0
C       10.6.100.12/30 is directly connected, Ethernet0/0
O       10.6.100.0/30 [110/20] via 10.6.100.5, 00:24:30, Ethernet0/1
O IA    10.6.101.0/30 [110/20] via 10.6.100.14, 00:24:30, Ethernet0/0
C       10.6.100.4/30 is directly connected, Ethernet0/1
O IA    10.6.201.0/24 [110/30] via 10.6.100.14, 00:24:31, Ethernet0/0
O IA    10.6.202.0/24 [110/20] via 10.6.1
```
Routeur5:
```
r5.tp6.b1#show ip route
Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route

Gateway of last resort is 10.6.101.1 to network 0.0.0.0

     10.0.0.0/8 is variably subnetted, 7 subnets, 2 masks
O IA    10.6.100.8/30 [110/20] via 10.6.101.1, 01:01:21, Ethernet0/0
O IA    10.6.100.12/30 [110/20] via 10.6.101.1, 01:01:12, Ethernet0/0
O IA    10.6.100.0/30 [110/30] via 10.6.101.1, 01:01:21, Ethernet0/0
C       10.6.101.0/30 is directly connected, Ethernet0/0
O IA    10.6.100.4/30 [110/30] via 10.6.101.1, 01:01:12, Ethernet0/0
C       10.6.201.0/24 is directly connected, Ethernet0/1
O IA    10.6.202.0/24 [110/40] via 10.6.101.1, 01:01:22, Ethernet0/0
O*E2 0.0.0.0/0 [110/1] via 10.6.101.1, 00:24:21, Ethernet0/0

```
* Faire un `curl google.com` depuis un des client:
```
[root@client1tp6 ~]# curl google.com
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="http://www.google.com/">here</A>.
</BODY></HTML>
```
* Faire une requête web vers un site full HTTP, avec résolution de nom depuis Routeur1:
```
r1.tp6.b1#telnet trip-hop.net 80
Translating "trip-hop.net"...domain server (8.8.8.8) [OK]
Trying trip-hop.net (213.186.33.4, 80)... Open
GET /
HTTP/1.1 400 Bad Request
Date: Tue, 12 Mar 2019 10:51:29 GMT
Cache-Control: no-cache
Content-Type: text/html
X-Cache: MISS from PF1-BOR1FR
X-Cache-Lookup: MISS from PF1-BOR1FR:3128
Connection: close

<html><body><h1>400 Bad request</h1>
                                    Your browser sent an invalid request.
                                                                         </body></html>

[Connection to trip-hop.net closed by foreign host]
```
## 2. Un service d'infra
* Faire un Curl sur Client1 de Serveur1:
```
[root@client1tp6 /]# curl serveur1tp6.b1
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
        <title>Test Page for the Nginx HTTP Server on Fedora</title>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
        <style type="text/css">
            /*<![CDATA[*/
            body {
                background-color: #fff;
                color: #000;
                font-size: 0.9em;
                font-family: sans-serif,helvetica;
                margin: 0;
                padding: 0;
            }
            :link {
                color: #c00;
            }
            :visited {
                color: #c00;
            }
            a:hover {
                color: #f50;
            }
            h1 {
                text-align: center;
                margin: 0;
                padding: 0.6em 2em 0.4em;
                background-color: #294172;
                color: #fff;
                font-weight: normal;
                font-size: 1.75em;
                border-bottom: 2px solid #000;
            }
            h1 strong {
                font-weight: bold;
                font-size: 1.5em;
            }
            h2 {
                text-align: center;
                background-color: #3C6EB4;
                font-size: 1.1em;
                font-weight: bold;
                color: #fff;
                margin: 0;
                padding: 0.5em;
                border-bottom: 2px solid #294172;
            }
            hr {
                display: none;
            }
            .content {
                padding: 1em 5em;
            }
            .alert {
                border: 2px solid #000;
            }

            img {
                border: 2px solid #fff;
                padding: 2px;
                margin: 2px;
            }
            a:hover img {
                border: 2px solid #294172;
            }
            .logos {
                margin: 1em;
                text-align: center;
            }
            /*]]>*/
        </style>
    </head>

    <body>
        <h1>Welcome to <strong>nginx</strong> on Fedora!</h1>

        <div class="content">
            <p>This page is used to test the proper operation of the
            <strong>nginx</strong> HTTP server after it has been
            installed. If you can read this page, it means that the
            web server installed at this site is working
            properly.</p>

            <div class="alert">
                <h2>Website Administrator</h2>
                <div class="content">
                    <p>This is the default <tt>index.html</tt> page that
                    is distributed with <strong>nginx</strong> on
                    Fedora.  It is located in
                    <tt>/usr/share/nginx/html</tt>.</p>

                    <p>You should now put your content in a location of
                    your choice and edit the <tt>root</tt> configuration
                    directive in the <strong>nginx</strong>
                    configuration file
                    <tt>/etc/nginx/nginx.conf</tt>.</p>

                </div>
            </div>

            <div class="logos">
                <a href="http://nginx.net/"><img
                    src="nginx-logo.png"
                    alt="[ Powered by nginx ]"
                    width="121" height="32" /></a>

                <a href="http://fedoraproject.org/"><img
                    src="poweredby.png"
                    alt="[ Powered by Fedora ]"
                    width="88" height="31" /></a>
            </div>
        </div>
    </body>
</html>
```
**YOUPI ça marche !!**
## 3. Serveur DHCP

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzUzOTE2MDY3LC0xNTYzMzQ4ODgzLC0xMj
Y5NTIwNjk2LC04MzQ5NDk3MywtMTAzMjQwNDQ1NCwtMjgzMzYx
NDM1LC0xMjQ2MTQ5NDIsLTE2MDA4NTY5ODIsLTEyNDM5MjU0Mj
IsMTk1NDcwMzc4NCw5NjM3NTA1NjIsOTA3Njg0MzgwLDczMDk5
ODExNl19
-->