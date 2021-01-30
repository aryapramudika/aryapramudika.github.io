# Konfigurasi Mikrotik Dasar


## Sekilas Tentang Mikrotik

Mikrotik merupakan sistem operasi Linux base yang diperuntukkan sebagai network router. Didesain untuk memberikan kemudahan bagi penggunanya. Administrasinya bisa dilakukan melalui Windows application (WinBox). Selain itu instalasi dapat dilakukan pada standard computer PC. PC yang akan dijadikan router mikrotik-pun tidak memerlukan resource yang cukup besar untuk penggunaan standard, misalnya hanya sebagai gateway. Untuk keperluan beban yang besar ( network yang kompleks, routing yang rumit dll) disarankan untuk mempertimbangkan pemilihan resource PC yang memadai.

### Jenis-Jenis Mikrotik

1. RouterOS

Mikrotik RouterOS adalah sistem operasi yang bisa digunakan untuk manajemen jaringan. Mikrotik RouterOS bisa di install di komputer yang berbasis X86,ARM64,ARM untuk lebih lengkapnya silahkan kunjungi web [Mikrotik](https://mikrotik.com/software)

2. RouterBoard

Mikrotik RouterBoard adalah pe rangkat keras yang dibuat khusus untuk menjalankan RouterOS,terdapat banyak sekali jenis RouterBoard ini untuk lebih detailnya silahkan kunjungi web [Mikrotik](https://mikrotik.com/products)


## Konfigurasi Dasar Mikrotik

### Persiapan
Untuk konfigurasi dasar mikrotik saya menggunakan GNS3 untuk simulasi jaringan dengan Mikrotik RouterOS.

Berikut gambar topologinya:

![Topologi](/img/mikrotik-topologi.png 'Topologi')

Terdapat dua cara untuk konfigurasi Router Mikrotik yang pertama bisa menggunakan Console/CLI kedua bisa menggunakan aplikasi Winbox, disini saya menggunakan Console/CLI.

### 1. Mengubah Nama Router Mikrotik
Kita dapat mengubah nama Router dengan perintah
```Console
/system identity set name=AryaRouter
```
![Memasukkan Perintah](/img/mikrotik-name.png 'Memasukkan Perintah')

disini saya mengubah nama Router **Mikrotik** menjadi **AryaRouter**

![Berhasil Mengubah Nama](/img/mikrotik-name1.png 'Nama Berhasil Diubah')

### 2. Reset Konfigurasi Mikrotik

Untuk melakukan reset konfigurasi saja maka bisa menggunakan soft reset

```
/system reset-configuration no-defaults=yes
```
![Softreset](/img/mikrotik-reset.png 'Memasukkan Perintah')

**Dangerous ! Reset anyway ?** ketik Y, lalu tunggu sampai muncul login Mikrotik dan Berhasil !!

![Softreset](/img/mikrotik-reset1.png 'Menunggu')

![Softreset](/img/mikrotik-login.png 'Reset berhasil')

Selanjutnya yaitu Hard Reset

Caranya,

1. Lepas kabel power
2. Lalu tekan tombol reset dengan tangan/pulpen tanpa dilepas, kemudian tancapkan kabel power dalam kondisi tombol reset masih ditekan
3. Tunggu lampu indikator sampai berhenti berkedip
4. Tunggu beberapa saat
5. Lalu cek dengan winbox/console.

Reset di Mikrotik Berhasil!

### 3. Konfigurasi IP Address
Disini saya menambahkan konfigurasi IP Address seperti di topologi yaitu di ether2

```
/ip address add address=172.16.1.1/24 interface=ether2
```
![Menambahkan IP](/img/mikrotik-ip1.png 'Menambahkan IP di Ether 2')

Kita gunakan perintah
```
/ip address print
```
Untuk melihat list IP Address yang ada di Router

![IP Berhasil Di Tambahkan](/img/mikrotik-ip.png 'Berhasil menambahkan IP di Ether 2')

Menambahkan IP Address Berhasil!

### 4. Konfigurasi NAT

Agar PC 1 kita bisa terhubung ke internet kita menggunakan fitur NAT Masquerade, untuk mengelabuhi internet agar bisa tersambung ke semua ether melalui ether 1

```
/ip firewall nat add chain=srcnat out-interface=ether1 action=masquerade
```
![Menambahkan IP Firewall](/img/mikrotik-nat11.png 'Memasukkan Perintah')

Perlu diperhatikan **out-interface** adalah interface yang terhubung ke internet.

![IP Firewall](/img/mikrotik-nat1.png 'NAT Masquerade berhasil dilakukan')

Untuk melihat NAT Masquerade berhasil ditambahkan yaitu dengan perintah

```
/ip firewall nat print
```

Konfigurasi NAT Masquerade Berhasil!

