====================================================
          Outil d'information réseau (netinfo)      
====================================================

Adresses IP des interfaces réseau
---------------------------------

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether **xx:xx:xx:xx:xx:xx** brd ff:ff:ff:ff:ff:ff
    inet **192.168.0.10/24** brd **192.168.0.255** scope global dynamic noprefixroute enp5s0
       valid_lft **XXXXsec** preferred_lft **XXXXsec**
    inet6 **2001:db8:abcd:1234:xxxx:xxxx:xxxx:xxxx/64** scope global temporary dynamic 
       valid_lft **XXXXsec** preferred_lft **XXXXsec**
    inet6 **2001:db8:abcd:1234:xxxx:xxxx:xxxx:xxxx/64** scope global dynamic mngtmpaddr noprefixroute 
       valid_lft **XXXXsec** preferred_lft **XXXXsec**
    inet6 **fe80::xxxx:xxxx:xxxx:xxxx/64** scope link noprefixroute 
       valid_lft forever preferred_lft forever

Routes IPv4
-----------
default via **192.168.0.1** dev enp5s0 proto dhcp src **192.168.0.10** metric 100 
**192.168.0.0/24** dev enp5s0 proto kernel scope link src **192.168.0.10** metric 100 

Routes IPv6
-----------
**2001:db8:abcd:1234::/64** dev enp5s0 proto ra metric 100 pref medium
**2001:db8:abcd:1200::/56** via **fe80::xxxx:xxxx:xxxx:xxxx** dev enp5s0 proto ra metric 100 pref medium
fe80::/64 dev enp5s0 proto kernel metric 1024 pref medium
default via **fe80::xxxx:xxxx:xxxx:xxxx** dev enp5s0 proto ra metric 100 pref medium

Serveurs DNS configurés
------------------------

**AAAA** **DD** **HH:MM:SS** **hostname** systemd[1]: Started systemd-resolved.service - Network Name Resolution.
**AAAA** **DD** **HH:MM:SS** **hostname** systemd-resolved[**PID**]: enp5s0: Bus client set default route setting: yes
**AAAA** **DD** **HH:MM:SS** **hostname** systemd-resolved[**PID**]: enp5s0: Bus client set DNS server list to: **[public-dns-1]**, **[public-dns-2]**, **[ipv6-public-dns-1]**, **[ipv6-public-dns-2]**
**AAAA** **DD** **HH:MM:SS** **hostname** systemd-resolved[**PID**]: enp5s0: Bus client set DNS server list to: **[public-dns-1]**, **[public-dns-2]**
**AAAA** **DD** **HH:MM:SS** **hostname** systemd-resolved[**PID**]: enp5s0: Bus client set search domain list to: **[search-domain]**

Statut du pare-feu
------------------

Votre système utilise nftables.

Voici les règles :

[sudo] password for **user**: 
Pare-feu IPv4
------------------

● Chaîne : INPUT
    		type filter hook input priority filter; policy drop;
    		iifname "lo" counter packets **[count]** bytes **[count]** accept
    		ct state related,established counter packets **[count]** bytes **[count]** accept
    		ip saddr **192.168.0.0/24** tcp dport 631 counter packets **[count]** bytes **[count]** accept
    		ip saddr **192.168.0.0/24** tcp dport 8000-8003 counter packets **[count]** bytes **[count]** accept
    		tcp dport 8000-8003 counter packets **[count]** bytes **[count]** drop
● Chaîne : FORWARD
    		type filter hook forward priority filter; policy drop;
● Chaîne : OUTPUT
    		type filter hook output priority filter; policy accept;

Pare-feu IPv6
------------------

● Chaîne : INPUT
    		type filter hook input priority filter; policy drop;
    		iifname "lo" counter packets **[count]** bytes **[count]** accept
    		ct state related,established counter packets **[count]** bytes **[count]** accept
    		meta l4proto ipv6-icmp counter packets **[count]** bytes **[count]** accept
    		udp dport 546 counter packets **[count]** bytes **[count]** accept
    		tcp dport 8000-8003 counter packets **[count]** bytes **[count]** drop
● Chaîne : FORWARD
    		type filter hook forward priority filter; policy drop;
● Chaîne : OUTPUT
    		type filter hook output priority filter; policy accept;

====================================================
              Fin du rapport netinfo                
====================================================

Souhaitez-vous exporter ce rapport ?
 - Pour un fichier texte local : netinfo txt
 - Pour un lien partageable :     netinfo nc
