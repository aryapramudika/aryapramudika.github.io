# Installasi Debian 10 Minimal Server


## Latar Belakang Masalah

Saya sedang belajar tentang debian server, terutama debian CLI. Saya sering lupa konfigurasi awal saat installasi debian untuk itu saya membuat tulisan ini.


## Tujuan

Tujuan saya menulis ini yaitu sebagai catatan belajar, jika saya lupa sesuatu maka saya bisa membaca tulisan ini.

## Persyaratan

Untuk persyaratan installasi yaitu:

1. Mempunyai koneksi Internet untuk mendownload iso CD/DVD Debian 10.

2. Perangkat Laptop/PC bisa juga Virtual seperti VirtualBox/VMWare

3. Untuk Laptop/PC membutuhkan flashdisk sebagai bootable minimal 8GB.

4. RAM 512 MB

5. Penyimpanan 2GB

## Membuat bootable pada flashdisk

Untuk installasi pada laptop/PC yang harus dilakukan pertama kali adalah membuat bootable di flashdisk.

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

{{< admonition tip "Tips" >}}
Kalian bisa membuat bootable menggunakan aplikasi lain seperti, [rufus](https://rufus.ie).
{{< /admonition >}}


## Installasi

Untuk penginstallan di PC/Laptop silahkan boot terlebih dahulu ke USB Bootable.

Disini saya melakukan penginstallan di VirtualMachine.

Langsung saja..

### 1. Pilih Metode Installasi

Disini saya menggunakan mode Install CLI, kalian bisa memilih menggunakan GUI kalau dirasa menggunakan CLI kurang nyaman.

![installasi](/img/p1-01installasi.png "Install / CLI")

### 2. Pilih Bahasa

Disini saya memilih bahasa Inggris

![installasi2](/img/p1-02installasi.png "English")

### 3. Pilih Country/Negara

Karena country Indonesia tidak ada di pilihan maka kita pilih **Other**

![installasi3](/img/p1-03installasi.png "Pilihan Other")

### 4. Pilih Continent/Region

Kita pilih **Asia**

![installasi4](/img/p1-04installasi.png "Pilihan Asia")

Lalu kita pilih **Indonesia**

![installasi5](/img/p1-05installasi.png "Pilihan Indonesia")

### 5. Konfigurasi Locale

Kita pilih **United States**

![installasi6](/img/p1-06installasi.png "Locale US")

### 6. Konfigurasi Keymap Keyboard

Kita pilih **American English**

![installasi7](/img/p1-07installasi.png "Pilihan American English")

### 7. Konfigurasi Hostname

Silahkan isi sesuai keinginan

![installasi8](/img/p1-08installasi.png "Hostname debsvr")

### 8. Konfigurasi Password Root

Isi password sesuai keinginan

![installasi9](/img/p1-09installasi.png "Root Password")

### 9. Konfigurasi User Baru

Isi sesuai keinginan

![installasi10](/img/p1-10installasi.png "Membuat user baru")

### 10. Konfigurasi Password untuk User Baru

Isi password sesuai keinginan

![installasi11](/img/p1-11installasi.png "Password user baru")

Masukkan password ulang

![installasi12](/img/p1-12installasi.png "Ulang Password user baru")

### 11.Konfigurasi Waktu

Sesuaikan dengan waktu wilayah masing-masing, karena saya WIB maka saya memilih **Western(Sumatra, Jakarta, Java, West and Central Kalimantan)**

![installasi13](/img/p1-13installasi.png "WIB")

### 12. Konfigurasi Partisi

Pilih **Guided Entire Disk**

![installasi14](/img/p1-14installasi.png "Guided")

Setelah itu pilih penyimpanan

![installasi15](/img/p1-15installasi.png "penyimpanan")

Lalu pada Partitioning Scheme kita pilih, **All files in one partition**

![installasi16](/img/p1-16installasi.png "Semua file di satu partisi")

Write Change to Disk? kita pilih **yes**

![installasi17](/img/p1-17installasi.png "Yes")

### 13. Menunggu Installasi Base System

![installasi18](/img/p1-18installasi.png "Menunggu installasi base system")

### 14. Konfigurasi Packet Manager

**Scan another CD or DVD?**

Pilih **No**

{{< admonition note "Catatan">}}
Jika kalian menggunakan iso DVD maka masukkan DVD yang lain misal: DVD 2 dan DVD 3
{{< /admonition >}}

![installasi19](/img/p1-19installasi.png "Pilihan No")

Untuk konfigurasi mirrorlist pilih **Indonesia**

![installasi20](/img/p1-20installasi.png "Mirrorlist Indonesia")

Lalu kita pilih salah satu, misal **kartolo.sby.datautama.net.id**

![installasi21](/img/p1-21installasi.png "Memilih Mirrorlist")

Pada HTTP Proxy kita kosongkan

![installasi22](/img/p1-22installasi.png "HTTP Proxy dikosongkan")

### 15. Konfigurasi Popularity Contest

**Participate in package usage survey?**, kita pilih **No**

![installasi23](/img/p1-23installasi.png "No")

### 16. Konfigurasi software

Pada menu **Choose Software to Install** hanya kita centang pada **SSH Server** dan **standard system utilities**

![installasi24](/img/p1-24installasi.png "Centang SSH dan standard system utilities")

Lalu kita tunggu installasi software selesai

![installasi25](/img/p1-25installasi.png "Installasi Software Selesai")

### 17. Konfigurasi Boot-loader

**Install the GRUB boot loader to the master boot record?** kita pilih **Yes**

![installasi26](/img/p1-26installasi.png "Yes")

Lalu kita pilih partisi yang kita buat tadi

![installasi27](/img/p1-27installasi.png "Pilih partisi")

Lalu kita tunggu dan installasi selesai..

![installasi28](/img/p1-29installasi.png "Berhasil")

Semoga membantu!!

