## etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.6
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1
```