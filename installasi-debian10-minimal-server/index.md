# Installasi Debian 10 Minimal Server


## Latar Belakang Masalah

Saya sedang belajar tentang debian server, terutama debian CLI. Saya sering lupa konfigurasi awal saat installasi debian untuk itu saya membuat tulisan ini.

## Tujuane

Tujuan saya menulis ini yaitu sebagai catatan belajar, jika saya lupa sesuatu maka saya bisa membaca tulisan ini.

## Persyaratan

Untuk persyaratan installasi yaitu:

1. Mempunyai koneksi Internet untuk mendownload iso CD/DVD Debian Buster.

2. Perangkat Laptop/PC bisa juga Virtual seperti VirtualBox/VMWare

3. Untuk Laptop/PC membutuhkan flashdisk sebagai bootable minimal 8GB.

4. RAM 512 MB

5. Penyimpanan 2GB

## Installasi 1 (Installasi Pada PC/Laptop)

### Membuat bootable pada flashdisk

Untuk membuat bootable saya menggunakan software balenaEtcher bisa di download di https://www.balena.io/etcher/

Pertama buka balenaEtcher lalu klik **Flash from file**

![balenaetcher](/img/p1-0bootable.png)

Kedua pilih file iso **Debian 10**

![balenaetcher](/img/p1-1bootable.png)

Ketiga klik **Select Target**

![balenaEtcher](/img/p1-2bootable.png)

Ke-empat pilih flashdisk yang dijadikan bootable

![balenaEtcher](/img/p1-3bootable.png)

Terakhir klik **Flash**, lalu tunggu sampai selesai

![balenaEtcher](/img/p1-4bootable.png)

![balenaEtcher](/img/p1-5bootable.png)

Pembuatan bootable berhasil

![balenaEtcher](/img/p1-6bootable.png)

### Installasi

