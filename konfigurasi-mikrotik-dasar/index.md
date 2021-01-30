# Konfigurasi Mikrotik Dasar


## Sekilas Tentang Mikrotik

Mikrotik merupakan sistem operasi Linux base yang diperuntukkan sebagai network router. Didesain untuk memberikan kemudahan bagi penggunanya. Administrasinya bisa dilakukan melalui Windows application (WinBox). Selain itu instalasi dapat dilakukan pada standard computer PC. PC yang akan dijadikan router mikrotik-pun tidak memerlukan resource yang cukup besar untuk penggunaan standard, misalnya hanya sebagai gateway. Untuk keperluan beban yang besar ( network yang kompleks, routing yang rumit dll) disarankan untuk mempertimbangkan pemilihan resource PC yang memadai.

### Jenis-Jenis Mikrotik

1. RouterOS

Mikrotik RouterOS adalah sistem operasi yang bisa digunakan untuk manajemen jaringan. Mikrotik RouterOS bisa di install di komputer yang berbasis X86,ARM64,ARM untuk lebih lengkapnya silahkan kunjungi web Mikrotik [RouterOS](https://mikrotik.com/software)

2. RouterBoard

Mikrotik RouterBoard adalah pe rangkat keras yang dibuat khusus untuk menjalankan RouterOS,terdapat banyak sekali jenis RouterBoard ini untuk lebih detailnya silahkan kunjungi web Mikrotik [RouterBoard](https://mikrotik.com/products)


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

![Softreset Berhasil](/img/mikrotik-reset1.png 'Soft Reset Berhasil')

Selanjutnya yaitu Hard Reset

Caranya,

1. Lepas kabel power
2. Lalu tekan tombol reset dengan tangan/pulpen tanpa dilepas, kemudian tancapkan kabel power dalam kondisi tombol reset masih ditekan
3. Tunggu lampu indikator sampai berhenti berkedip
4. Tunggu beberapa saat
5. Lalu cek dengan winbox/console.

Reset di Mikrotik Berhasil Dilakukan

### Konfigurasi IP Address


