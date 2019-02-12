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

```
* Client2:
```

```
* Serveur1:
```
[root@serveur ~]# hostname
serveur.1
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NDMwMzYzOTYsNzMwOTk4MTE2XX0=
-->