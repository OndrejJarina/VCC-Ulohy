# NI-VCC Úloha 2
#### Ondrej Jarina, 2023

Z minulej úlohy máme nasadené 2 virtuálne stroje na rôznych hostiteľoch.
![](img/instancie_z_ulohy_1.png)

Pomocou príkazu `ip route` zistíme adresu DHCP servera na riadiacom uzle

![](img/ip_route1.png)

Z virtuálneho stroja spustíme ping na DHCP server.

![](img/dhcp_ping.png)

### XML deskriptor
XML deskriptior VM získame po vstúpení do konzoly kontajnera nova_libvirt príkazom `docker exec -it nova_libvirt bash -i`,
pomocou príkazu `virsh list` získame zoznam VM spustených na host uzle.

![](img/virsh_list.png)

Inštancia má názov instance-0000005, jej XML deskriptor nájdeme teda na adrese `/etc/libvirt/qemu/instance-00000005.xml`. 
Príkazom `cat` zistíme jeho obsah.

![](img/interface.png)

* **názov tap rozhrania:** tap9af5ad8d-92
* **názov bridge rozhrania:** qbr9af5ad8d-92

### Trasovanie prevádzky pomocou tcpdump

Trasovanie prevádzky môžeme vykonať pomocou príkazu `tcpdump -i` na rozhraní `tap9af5ad8d-92`
Vidíme prechádzajúce packety pingu na dhcp server.
![](img/tcp_dump_dhcp.png)

Ak chceme zistiť, či ping prechádza firewallom, trasujeme prevádzku na rozhraní qvb zo strany bridgeu, teda `qvb9af5ad8d-92`

![](img/tcp_dump_dhcp_qvb.png)

### Trasovanie prevádzky pomocou Wireshark


