# Installasi Packettracer Di Arch Linux/Based


## Sekilas tentang PacketTracer

Packet Tracer adalah simulator alat-alat jaringan Cisco yang sering digunakan sebagai media pembelajaran dan pelatihan, dan juga dalam bidang penelitian simulasi jaringan komputer. Program ini dibuat oleh Cisco Systems dan disediakan gratis untuk fakultas, siswa dan alumni yang telah berpartisipasi di Cisco Networking Academy. Tujuan utama Packet Tracer adalah untuk menyediakan alat bagi siswa dan pengajar agar dapat memahami prinsip jaringan komputer dan juga membangun skill di bidang alat-alat jaringan Cisco.

## Persiapan

 Pastikan sudah menginstall Git:

 ```bash
sudo pacman -Sy git
```
## Installasi dan Konfigurasi

Clone PKGBuild dari AUR

```bash
cd ~
git clone https://aur.archlinux.org/packettracer.git
```
Lalu download PacketTracer berformat .deb di website [Netacad](https://www.netacad.com/portal/resources/packet-tracer) pastikan sudah membuat akun netacad.

![packettracer1](/img/packettracer0.png 'Download Packettracer Versi Linux')

Setelah itu copy/pindah file PacketTracer.deb ke folder packettracer yang kita clone tadi

![packettracer2](/img/packettracer1.png 'Pindah File .deb ke folder packettracer')

lalu buka folder packettracer di terminal

![packettracer3](/img/packettracer2.png 'Buka folder packettracer di terminal')

dan jalankan perintah

```bash
makepkg -si
```
Lalu tunggu sampai installasi berhasil

![packettracer4](/img/packettracer3.png 'Menunggu installasi selesai')

Installasi Berhasil!

![packettracer5](/img/packettracer4.png 'Installasi Berhasil!')

## Selesai

Selamat mencoba!

jika ada error atau masalah silakan diskusikan di bawah

## Referensi

* https://wiki.archlinux.org/index.php/PacketTracer

* https://id.m.wikipedia.org/wiki/Packet_Tracer

