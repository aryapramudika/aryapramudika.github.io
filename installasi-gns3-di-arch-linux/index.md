# Installasi Gns3 Di Arch Linux


## Latar Belakang

Saya ingin menginstall GNS3 di Arch Linux tapi belum ada artikel bahasa Indonesia yang membahas jadi saya tulis saja disini.

## Tujuan

Agar memudahkan pengguna Arch Linux untuk Installasi Gns3

## Persiapan

Pastikan sudah terinstall AUR Helper, disini saya menggunakan yay.

Berikut cara installasi yay

```bash
cd ~ && sudo pacman -Sy && sudo pacman -S git && sudo pacman -S base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

{{< admonition note "Penjelasan Perintah">}}

**cd ~** pindah direktori ke home

**sudo pacman -Sy** melakukan update repository

**sudo pacman -S git** installasi git

**sudo pacman -S base-devel** installasi base-devel

**git clone https://aur.archlinux.org/yay.git** clone package yay dari AUR

**cd yay** pindah ke direktori yay

**makepkg -si** melakukan installasi yay

{{< /admonition >}}

