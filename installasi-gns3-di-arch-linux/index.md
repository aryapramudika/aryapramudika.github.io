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

> Output Perintah : Cisco Router Simulation Platform (version 0.2.21-amd64/Linux stable)

```bash
getcap $(which dynamips)
```

> Output Perintah : /usr/bin/dynamips cap_net_admin,cap_net_raw=ep

### 2. Installasi VPCS

```bash
yay -S vpcs --nodiffmenu --noeditmenu --nocleanmenu
```

Memastikan VPCS terinstall

```bash
 cd ~ && type vpcs
```

> Output Perintah: vpcs is /usr/bin/vpcs

```bash
vpcs -v | grep version
```
> Output Perintah: Welcome to Virtual PC Simulator, version 0.8 beta

### 3. Installasi IOL untuk Simulasi Cisco

Pastikan sudah mengaktifkan repo lib32 di */etc/pacman.conf*

```bash
sudo pacman -Sy lib32-openssl lib32-gcc-libs && sudo ln -s /usr/lib32/libcrypto.so.1.0.0 /usr/lib32/libcrypto.so.4
```
Mencegah jika nanti terjadi error di EXCESSCOLL

```bash
sudo sysctl net.unix.max_dgram_qlen=10000
```
Konfigurasi Permanen

```bash
sudo tee -a /etc/sysctl.d/99-sysctl.conf > /dev/null << EOL

net.unix.max_dgram_qlen=10000

EOL
```
> setelah perintah pertama lalu masukkan > net.unix.max-dgram_qlen & > EOL

Memastikan konfigurasi IOL

```bash
sysctl net.unix.max_dgram_qlen
```
> Output Perintah: net.unix.max_dgram_qlen = 10000

```bash
tail -2 /etc/sysctl.d/99-sysctl.conf
```
> Output Perintah: net.unix.max_dgram_qlen=10000

