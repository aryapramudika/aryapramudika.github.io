# Setup Samba Server Debian 10


## Latar Belakang

Saya sedang belajar tentang Samba Server dan ingin mencatatnya disini.

## Tujuan

Agar saya lebih mahir dan paham tentang konfigurasi Samba Server

## Sekilas tentang Samba

> Samba adalah program yang bersifat open source yang menyediakan layanan berbagi berkas (file service) dan berbagi alat pencetak (print service), resolusi nama NetBIOS, dan pengumuman layanan (NetBIOS service announcement/browsing). Sebagai sebuah aplikasi file server, Samba mengizinkan berkas, alat pencetak, dan beberapa sumber daya lainnya agar dapat digunakan oleh banyak pengguna dalam keluarga sistem operasi UNIX, dan mengizinkan interoperabilitas dengan sistem operasi Windows. Intinya dengan menggunakan Samba server file sharing bisa multi platform antara UNIX dan Windows.

## Konfigurasi

Pertama kita perlu install paket samba

```bash
apt -y install samba
```

Setelah itu kita lakukan konfigurasi di */etc/samba/smb.conf*

```bash
nano /etc/samba/smb.conf
```

Buat konfigurasi setelah baris paling bawah

Contoh konfigurasi

```bash
[Share Film]
    comment = Share film lokal
    path = /film
    browseable = yes
    read only = no
    guest ok = yes
```

{{< admonition note "Penjelasan">}}
*[Share Film]* adalah nama konfigurasi sharing bisa di custom sesuai keinginan.

*comment = Share film lokal* adalah penjelasan apa yang di share misal "Share film lokal".

*path = /film* adalah lokasi folder yang kita share misal root/film.

*browseable = yes* adalah berarti kita mengizinkan konfigurasi sharing kita di akses.

*read-only = no* adalah bahwa folder yang kita share tidak hanya bisa di lihat tapi bisa diubah.

*guest ok = yes* adalah mengizinkan semua orang bisa mengakses sharing kita secara anonymous atau tanpa use

{{< /admonition >}}

Setelah konfigurasi maka kita wajib melakukan restart pada service Samba

```bash
service smbd restart
```
Konfigurasi Samba Server selesai, lanjut ke Samba Client

## Konfigurasi Klien

di sini klien saya menggunakan OS Ubuntu 20.04,

Pertama lakukan installasi paket *samba-client* & *cifs-utils*

```bash
sudo apt -y install samba-client cifs-utils
```
untuk mengakses Samba Server terdapat 2 cara yaitu:

### 1. Mengakses dengan File Manager

Buka File Manager

![File Manager](/img/smb01.png)

lalu tekan *Ctrl+L*

![CTRL+L](/img/smb02.png)

setelah itu masukkan

```bash
smb://ipserver
```
![IP Server](/img/smb03.png)

Lalu tekan enter, dan muncul folder dari Samba Server kita pilih folder Share Film

![Muncul](/img/smb04.png)

Lalu *connect as Anonymous* dan klik **Connect**

![Connect](/img/smb05.png)

dan berhasil

![Berhasil](/img/smb06.png)

### 2 Mengakses dengan Terminal

* Mounting Sementara

Pertama buat folder untuk Mounting

```bash
mkdir /home/arya/film
```

Lalu lihat list Samba Server menggunakan perintah

```bash
smbclient -L 192.168.1.233
```
dan tekan enter

![melihat samba sever](smbc01.png)

Lalu mount nama Samba Server ke folder */home/arya/film*

```bash
sudo mount //192.168.1.233/ /home/arya/film
```
dan tekan enter

* Mounting Permanen

Edit file */etc/fstab*

```bash
sudo nano /etc/fstab
```
Lalu tambahkan konfigurasinya setelah baris paling bawah

```bash
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=13001d90-f605-4673-b8d2-faa228380464 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=B6CD-AEA1  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#mount ke DIR
#10.10.10.2:/test	/home/arya/DIR		nfs4	netdev

#mount ke nfs2
#10.10.10.2:/nfs2	/home/arya/nfs2		nfs4	rw

# Samba
//192.168.1.233/Share\ Film   /home/arya/film   cifs    netdev
```

## Selesai

Konfigurasi Samba berhasil dilakukan

Selamat Mencoba !!

## Referensi

* https://linuxconfig.org/how-to-set-up-a-samba-server-on-debian-10-buster#h4-configure-a-new-share

* https://help.ubuntu.com/community/Samba/SambaClientGuide

* https://askubuntu.com/questions/1050460/how-to-mount-smb-share-on-ubuntu-18-04

