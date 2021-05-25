# Membangun Router Sederhana dengan OpenBSD



## Prasyarat

1. OpenBSD
2. Internet

## Konfigurasi Interface

```Shell
buntal# ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 32768
        index 4 priority 0 llprio 3
        groups: lo
buntal# ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 32768
        index 4 priority 0 llprio 3
        groups: lo
        inet6 ::1 prefixlen 128
        inet6 fe80::1%lo0 prefixlen 64 scopeid 0x4
        inet 127.0.0.1 netmask 0xff000000
em0: flags=808843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST,AUTOCONF4> mtu 1500
        lladdr 52:54:00:84:f2:79
        index 1 priority 0 llprio 3
        groups: egress
        media: Ethernet autoselect (1000baseT full-duplex)
        status: active
        inet 192.168.122.224 netmask 0xffffff00 broadcast 192.168.122.255
em1: flags=8802<BROADCAST,SIMPLEX,MULTICAST> mtu 1500
        lladdr 52:54:00:f7:05:b0
        index 2 priority 0 llprio 3
        media: Ethernet autoselect (1000baseT full-duplex)
        status: active
enc0: flags=0<>
        index 3 priority 0 llprio 3
        groups: enc
        status: active
pflog0: flags=141<UP,RUNNING,PROMISC> mtu 33136
        index 5 priority 0 llprio 3
        groups: pflog
```
      
Disini sumber internet dari **em0**, **em1** akan saya konfigurasi sebagai dhcp server untuk client

### Konfigurasi IP Static di **em1**

Disini saya menggunakan IP 192.168.1.0/24 untuk di distribusikan ke client


```Shell
echo 'inet 192.168.1.1 255.255.255.0 NONE' >> /etc/hostname.em1
```
Ubah File Permission menjadi 640

```Shell
chmod 640 /etc/hostname.em1
```

Lalu Restart Interface em1

```Shell
sh /etc/netstart em1
```

### Enable IP Forwarding

```Shell
echo 'net.inet.ip.forwarding=1' > /etc/sysctl.conf
```

## Konfigurasi DHCP Server

Copy file example dari /etc/example

```Shell
cp /etc/example/dhcpd.conf /etc/dhcpd.conf
```

Edit file, disini saya menggunakan nano

```Shell
nano /etc/dhcpd.conf
```
``` Output
#       $OpenBSD: dhcpd.conf,v 1.1 2014/07/11 21:20:10 deraadt Exp $
#
# DHCP server options.
# See dhcpd.conf(5) and dhcpd(8) for more information.
#

# Network:              192.168.1.0/255.255.255.0
# Domain name:          my.domain
# Name servers:         192.168.1.3 and 192.168.1.5
# Default router:       192.168.1.1
# Addresses:            192.168.1.32 - 192.168.1.127
#
option  domain-name "my.domain";
option  domain-name-servers 192.168.1.3, 192.168.1.5;

subnet 192.168.1.0 netmask 255.255.255.0 {
        option routers 192.168.1.1;

        range 192.168.1.32 192.168.1.127;

        host static-client {
                hardware ethernet 22:33:44:55:66:77;
                fixed-address 192.168.1.200;
        }

        host pxe-client {
                hardware ethernet 02:03:04:05:06:07;
                filename "pxeboot";
                next-server 192.168.1.1;
        }
}
```

Saya mengubah domain-name router menjadi **buntal.local** dengan dns server isp **192.168.122.1**

Saya tidak perlu ip tetap di client tertentu jadi saya hapus konfigurasi **host static-client**, **host static-pxe-client**

Saya ubah range IP menjadi 192.168.1.2-192.168.1.254

Hasil Akhir

```Shell
#       $OpenBSD: dhcpd.conf,v 1.1 2014/07/11 21:20:10 deraadt Exp $
#
# DHCP server options.
# See dhcpd.conf(5) and dhcpd(8) for more information.
#

# Network:              192.168.1.0/255.255.255.0
# Domain name:          my.domain
# Name servers:         192.168.1.3 and 192.168.1.5
# Default router:       192.168.1.1
# Addresses:            192.168.1.32 - 192.168.1.127
#
option  domain-name "buntal.local";
option  domain-name-servers 192.168.122.1;

subnet 192.168.1.0 netmask 255.255.255.0 {
        option routers 192.168.1.1;
        range 192.168.1.2 192.168.1.254;
}

```
Enable dan start dhcpd services

```Shell
buntal# rcctl enable dhcpd && rcctl start dhcpd                         
dhcpd(ok)
```
Mohon maaf kalau ada kekurangan

## Referensi

* https://openbsdrouterguide.net/
* https://www.cyberciti.biz/faq/openbsd-restart-network/
* google.com

