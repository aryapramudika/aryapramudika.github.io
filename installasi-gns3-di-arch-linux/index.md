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

selanjutnya ke tahap Installasi

## Installasi

### 1. Install Dynamips serta package yang dibutuhkan

```bash
sudo pacman -S libelf libpcap cmake && yay -S dynamips --nodiffmenu --noeditmenu --nocleanmenu && sudo setcap cap_net_admin,cap_net_raw=ep $(which dynamips)
```

Memastikan Dynamips sudah terinstall

```bash
cd ~ && dynamips 2> /dev/null | grep version
```

> Output : Cisco Router Simulation Platform (version 0.2.21-amd64/Linux stable)

