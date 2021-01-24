# Installasi DHCP Server Debian 10


## Sekilas tentang DHCP

Apa itu DHCP? saya kutip dari wikipedia

> **Dynamic Host Configuration Protocol** adalah protokol yang berbasis arsitektur client/server yang dipakai untuk memudahkan pengalokasian alamat IP dalam satu jaringan.

## Konfigurasi

Pertama lakukan installasi packet *isc-dhcp-server*

```bash
apt -y install isc-dhcp-server
```
> Jika muncul peringatan failed setelah install itu terjadi karena ip kita tidak sesuai dengan IP Address pada konfigurasi isc-dhcp-server, untuk itu **abaikan** saja.

Lalu lakukan konfigurasi interface yang akan dijadikan DHCP Server

```bash
nano /etc/default/isc-dhcp-server
```
Tambahkan nama interface di INTERFACESv4, lalu beri tanda **#** pada INTERFACESv6

```bash
# Defaults for isc-dhcp-server (sourced by /etc/init.d/isc-dhcp-server)

# Path to dhcpd's config file (default: /etc/dhcp/dhcpd.conf).
#DHCPDv4_CONF=/etc/dhcp/dhcpd.conf
#DHCPDv6_CONF=/etc/dhcp/dhcpd6.conf

# Path to dhcpd's PID file (default: /var/run/dhcpd.pid).
#DHCPDv4_PID=/var/run/dhcpd.pid
#DHCPDv6_PID=/var/run/dhcpd6.pid

# Additional options to start dhcpd with.
#	Don't use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
#OPTIONS=""

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACESv4="ens33" #isi nama interface disini
#INTERFACESv6=""
```

Setelah itu kita lakukan konfigurasi IP Address

```bash
nano /etc/dhcpd.dhcpd.conf
```

Lakukan konfigurasi pada baris ke 49 sampai 58,

* Default

```bash
# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
  #range 10.5.5.26 10.5.5.30;
  #option domain-name-servers ns1.internal.example.org;
  #option domain-name "internal.example.org";
  #option routers 10.5.5.1;
  #option broadcast-address 10.5.5.31;
  #default-lease-time 600;
  #max-lease-time 7200;
#}
```
* Setelah Dikonfigurasi

```bash
# A slightly different configuration for an internal subnet.
subnet 10.10.10.0 netmask 255.255.255.0 {
  range 10.10.10.2 10.10.10.100;
  option domain-name-servers 8.8.8.8;
  option domain-name "arya.com";
  option routers 10.10.10.1;
  option broadcast-address 10.10.10.255;
  default-lease-time 600;
  max-lease-time 7200;
}
```
{{< admonition note "Catatan">}}
Konfigurasikan sesuai dengan keinginan, di **Interface ens33** ip saya yaitu 10.10.10.1

**range** yaitu batas awal dan terakhir yang akan di berikan

**domain-name-servers** bisa di isi 8.8.8.8 atau **IP Interface**

**domain-name** bisa di custom

**routers** di isi **IP Interface**

**broadcast-address** batas maksimal ip dari subnet
{{< /admonition >}}

