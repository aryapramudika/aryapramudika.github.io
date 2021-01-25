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

Setelah itu kita edit konfigurasinya di */etc/samba/smb.conf*

```bash
nano /etc/samba/smb.conf
```

