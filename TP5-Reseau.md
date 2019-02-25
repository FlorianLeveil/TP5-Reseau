# TP 5 - Premier pas dans le monde Cisco
# I. Préparation du lab
## 1. Préparation VMs
**2. Création des VMs + Réseau:**
* Client1:
```
[root@client ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:87:3f:40 brd ff:ff:ff:ff:ff:ff
    inet 10.5.2.10/24 brd 10.5.2.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe87:3f40/64 scope link
       valid_lft forever preferred_lft forever
```
* Client2:
```
[root@client ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:87:3f:40 brd ff:ff:ff:ff:ff:ff
    inet 10.5.2.11/24 brd 10.5.2.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe87:3f40/64 scope link tentative dadfailed
       valid_lft forever preferred_lft forever
```
* Serveur1:
```
[root@serveur ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:87:3f:40 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.10/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe87:3f40/64 scope link
       valid_lft forever preferred_lft forever
```
# II. Lancement et configuration du lab
## Checklist IP VMs
**Nom de domaine**
* Client1:
```
[root@client ~]# hostname
client.1
```
* Client2:
```
[root@client ~]# hostname
client.2
```
* Serveur1:
```
[root@serveur ~]# hostname
serveur.1
```
**Connexion SSH carte réseau enps08**
* Client1:
```
[root@client ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:87:3f:40 brd ff:ff:ff:ff:ff:ff
    inet 10.5.2.10/24 brd 10.5.2.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe87:3f40/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:51:38:07 brd ff:ff:ff:ff:ff:ff
    inet 192.168.67.5/24 brd 192.168.67.255 scope global noprefixroute dynamic enp0s8
       valid_lft 814sec preferred_lft 814sec
    inet6 fe80::de46:ef48:daa0:432a/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```
* Client2:
```
[root@client ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:87:3f:40 brd ff:ff:ff:ff:ff:ff
    inet 10.5.2.11/24 brd 10.5.2.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe87:3f40/64 scope link tentative dadfailed
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:8f:07:fd brd ff:ff:ff:ff:ff:ff
    inet 192.168.67.4/24 brd 192.168.67.255 scope global noprefixroute dynamic enp0s8
       valid_lft 840sec preferred_lft 840sec
    inet6 fe80::8baf:e214:17e2:bde4/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```
* Serveur1:
```
[root@serveur ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:87:3f:40 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.10/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe87:3f40/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:86:d2:00 brd ff:ff:ff:ff:ff:ff
    inet 192.168.67.3/24 brd 192.168.67.255 scope global noprefixroute dynamic enp0s8
       valid_lft 852sec preferred_lft 852sec
    inet6 fe80::7d34:91dd:ff58:c240/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```
## Checklist IP Routeurs
**Définition des IP Statiques**
* Routeur1:
```
routeur1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.5.1.254      YES manual up                    up
Ethernet0/1                10.5.12.1       YES manual up                    up
Ethernet0/2                unassigned      YES unset  administratively down down
Ethernet0/3                unassigned      YES unset  administratively down down

```
* Routeur2:
```
routeur2#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.5.2.254      YES manual up                    up
Ethernet0/1                10.5.12.2       YES manual up                    up
Ethernet0/2                unassigned      YES unset  administratively down down
Ethernet0/3                unassigned      YES unset  administratively down down

```
**Définition des Noms de Domaines**
* Routeur1:
```
routeur1#
routeur1#show startup-config
Using 887 out of 260088 bytes
!
version 12.4
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname routeur1
```
Routeur1 est devenue routeur2.

* Routeur2:
```
routeur2#
*Mar  1 00:42:37.815: %SYS-5-CONFIG_I: Configured from console by console
routeur2#copy running-config startup-config
Destination filename [startup-config]?
Building configuration...
[OK]
routeur2#show startup-config
Using 887 out of 260088 bytes
!
version 12.4
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname routeur2

```
Routeur2 est devenue routeur2.

## Checklist routes
router1:
-   Rajouter `net2`
```
routeur1#show ip route
Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route

Gateway of last resort is 10.5.12.2 to network 0.0.0.0

     10.0.0.0/8 is variably subnetted, 3 subnets, 2 masks
C       10.5.12.0/30 is directly connected, Ethernet0/1
S       10.5.2.0/24 [1/0] via 10.5.12.2
C       10.5.1.0/24 is directly connected, Ethernet0/0
S*   0.0.0.0/0 [1/0] via 10.5.12.2

```
router2:
-   Rajouter `net1`
```
routeur2#show ip route
Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route

Gateway of last resort is 10.5.12.1 to network 0.0.0.0

     10.0.0.0/8 is variably subnetted, 3 subnets, 2 masks
C       10.5.12.0/30 is directly connected, Ethernet0/1
C       10.5.2.0/24 is directly connected, Ethernet0/0
S       10.5.1.0/24 [1/0] via 10.5.12.1
S*   0.0.0.0/0 [1/0] via 10.5.12.1

```
serveur1:
-   Rajouter `net2`
```
[root@serveur ~]# ip route show
10.5.1.0/24 dev enp0s3 proto kernel scope link src 10.5.1.10 metric 102
10.5.2.0/24 via 10.5.1.254 dev enp0s3 proto static metric 102
192.168.67.0/24 dev enp0s8 proto kernel scope link src 192.168.67.3 metric 101
```
client1:
-   Rajouter `net1`
```
[root@client network-scripts]# ip route show
10.5.1.0/24 via 10.5.2.254 dev enp0s3 proto static metric 102
10.5.2.0/24 dev enp0s3 proto kernel scope link src 10.5.2.10 metric 102
192.168.67.0/24 dev enp0s8 proto kernel scope link src 192.168.67.5 metric 101
```
client2:
-   Rajouter `net1`
```
[root@client ~]# ip route show
10.5.1.0/24 via 10.5.2.254 dev enp0s3 proto static metric 102
10.5.2.0/24 dev enp0s3 proto kernel scope link src 10.5.2.11 metric 102
192.168.67.0/24 dev enp0s8 proto kernel scope link src 192.168.67.4 metric 101
```
### Teste:
Client1 > Serveur1
```
ping server1.tp5.b1
PING server1.tp5.b1 (10.5.1.10) 56(84) bytes of data.
64 bytes from server1.tp5.b1 (10.5.1.10): icmp_seq=2 ttl=62 time=27.5 ms
```
Client2 > Serveur1
```
ping server1.tp5.b1
PING server1.tp5.b1 (10.5.1.10) 56(84) bytes of data.
64 bytes from server1.tp5.b1 (10.5.1.10): icmp_seq=1 ttl=62 time=31.5 ms
64 bytes from server1.tp5.b1 (10.5.1.10): icmp_seq=2 ttl=62 time=24.3 ms
```
# III. DHCP
## 1. Mise en place du serveur DHCP
### 1.  Renommer la machine
```
[root@client ~]# nano /etc/hostname
hostname dhcp-net2.tp5.b1
```
### 2. Installer le serveur DHCP
-   éteindre la VM dans GNS3
-   ouvrir VirtualBox
-   ajouter une troisième carte en NAT à la VM
-   démarrer la VM dans VirtualBox
```
[root@dhcp-net2 ~]# yum install -y dhcp
```
### 4. Configuration du serveur DHCP

Dans le fichier `sudo nano /etc/dhcp/dhcpd.conf` de dhcp-net2 :
```
# dhcpd.conf
# option definitions common to all supported networks

option domain-name "tp5.b1";
default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.

authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).

log-facility local7;
subnet 10.5.2.0 netmask 255.255.255.0 {
range 10.5.2.50 10.5.2.70;
option domain-name "tp5.b1";
option routers 10.5.2.254;
option broadcast-address 10.5.2.255;
}
```
### 5. Démarrer le serveur DHCP
```
[root@dhcp-net2 ~]# systemctl start dhcpd
```
Verification:

```
[root@dhcp-net2 ~]# systemctl status dhcpd -l
● dhcpd.service - DHCPv4 Server Daemon
   Loaded: loaded (/usr/lib/systemd/system/dhcpd.service; enabled; vendor preset: disabled)
   Active: active (running) since mer. 2019-02-20 17:27:20 CET; 2min 48s ago
     Docs: man:dhcpd(8)
           man:dhcpd.conf(5)
 Main PID: 3881 (dhcpd)
   Status: "Dispatching packets..."
   CGroup: /system.slice/dhcpd.service
           └─3881 /usr/sbin/dhcpd -f -cf /etc/dhcp/dhcpd.conf -user dhcpd -group dhcpd --no-pid

févr. 20 17:27:20 dhcp-net2.tp5.b1 dhcpd[3881]: Listening on LPF/eth0/00:50:00:00:05:00/10.5.2.0/24
févr. 20 17:27:20 dhcp-net2.tp5.b1 dhcpd[3881]: Sending on   LPF/eth0/00:50:00:00:05:00/10.5.2.0/24
févr. 20 17:27:20 dhcp-net2.tp5.b1 dhcpd[3881]: Sending on   Socket/fallback/fallback-net
févr. 20 17:27:20 dhcp-net2.tp5.b1 systemd[1]: Started DHCPv4 Server Daemon.
```
### 6. Faire un test
Sur client1 :

-   IP dynamique  `sudo nano /etc/sysconfig/network-scripts/ifcfg-enp0s3`

```
NAME=enp0s3
DEVICE=enp0s3

BOOTPROTO=dhcp
ONBOOT=yes
```
* `ip a`:
```
enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:35:66:94 brd ff:ff:ff:ff:ff:ff
    inet 10.5.2.50/24 brd 10.5.2.255 scope global noprefixroute dynamic enp0s3
       valid_lft 598sec preferred_lft 598sec
    inet6 fe80::a00:27ff:fe35:6694/64 scope link
       valid_lft forever preferred_lft forever
```
# IV. Bonus
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NTY5NTg5NDYsMTI1ODI0NjkxLC04NT
c4MjExNTEsMzUwMTgzODUsMjA2Mjc5MTAzOSw1NDk5NTY0MTEs
LTE0MDc3OTI5NTcsLTE1OTU0MzU0MDQsMTc4OTE5MzU2NSw4OD
k5ODI2NjgsLTMxMDI5ODQxOCw4ODAzNjA1OCwtMTEwNzQwMzA5
NSwtMTkwMjI3NTA4LDIwOTk3NjA5NDQsNzMwOTk4MTE2XX0=
-->