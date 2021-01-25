# Setup NFS Server Debian 10


## Latar Belakang

Saya sedang belajar tentang NFS Server pada Debian dan ingin mencatatnya disini.

## Tujuan

Agar tetap ingat konfigurasi tentang NFS Server.

## Sekilas tentang NFS

> Network File Sharing adalah sebuah kumpulan protokol yang digunakan untuk mengakses beberapa sistem berkas melalui jaringan. NFS umumnya hanya bisa bekerja di *UNIX* Sistem, untuk di Windows tidak menggunakan NFS melainkan SMB (Server Message Block) sehingga tidak kompatibel dengan sistem NFS. Untuk SMB kita akan bahas di artikel berikutnya..

## Konfigurasi NFS

Pertama kita perlu melakukan installasi paket *nfs-kernel-server*

```bash
apt -y install nfs-kernel-server
```
Setelah itu kita lakukan konfigurasi

```bash
nano /etc/exports
```

* Konfigurasi Default

```bash
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
```
Lalu kita buat folder sharing nya misal di directory /

```bash
mkdir /nfs3
```

Setelah itu kita tambahkan setelah baris bawah sendiri untuk konfigurasinya

```bash
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/nfs3   */(rw,sync)
```

>Untuk format penulisan konfigurasi-nya kurang lebih seperti ini
*/directory/to/share machine1(option1,option2,...) machine2(...) ...*

{{< admonition note "Penjelasan Konfigurasi">}}
*/nfs3* berarti yang jadikan nfs server adalah directory root/nfs3

*/    berarti kita mengizinkan semua komputer bisa mengakses NFS Server

*(rw,sync)* rw berarti *read/write* lalu *sync* berarti antara Server dan Klien akan selalu melakukan sinkronisasi

Untuk lebih detail nya bisa kunjungi:

*  https://man7.org/linux/man-pages/man5/nfs.5.html
{{< /admonition >}}

## Konfigurasi pada Klien

Pertama kita perlu melakukan intallasi paket *nfs-common*

```bash
apt -y install nfs-common
```

Untuk mengakses NFS Server terdapat dua cara yaitu:

### 1. Mounting Manual dari Terminal

Buat folder untuk mounting

```bash
mkdir /home/arya/sharing
```

Lalu kita lakukan perintah

```bash
mount 10.10.10.2:/nfs3   /home/arya/sharing
```
{{< admonition note "Penjelasan">}}

*10.10.10.2* adalah IP Interface

*:/nfs3* adalah folder yang di share

*/home/arya/sharing* adalah folder yang kita mount ke server.

{{< /admonition >}}

Mounting manual selesai, kekurangan dari metode ini adalah tidak permanen, setelah kita reboot maka kita wajib melakukan mounting ulang.

### 2. Mounting permanen

Edit file */etc/fstab*

```bash
nano /etc/fstab
```

Lalu tambahkan di baris paling bawah

```bash
10.10.10.2:/nfs3      /home/arya/Sharing      nfs     _netdev     
```
{{< admonition note "Penjelasan">}}

*10.10.10.2* adalah IP server

*:/nfs3* adalah folder yang di share.

*/home/arya/sharing* adalah folder yang kita mount ke server.

*nfs* adalah tipe file/folder.

*_netdev* adalah mounting akan berjalan jika kita terhubung ke jaringan.

{{< /admonition >}}

## Selesai!

Konfigurasi NFS Server di Debian 10 berhasil!!

Selamat mencoba !!

