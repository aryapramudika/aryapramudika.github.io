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

di sini saya menggunakan OS Ubuntu 20.04, untuk mengakses Samba Server terdapat 2 cara yaitu:

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




## Selesai

Konfigurasi Samba kita berhasil dilakukan

