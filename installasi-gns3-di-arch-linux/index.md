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

Untuk installasi kita perlu menginstall package satu persatu

### 1. Install Dynamips Serta Package Yang Dibutuhkan

```bash
sudo pacman -S libelf libpcap cmake && yay -S dynamips --noconfirm && sudo setcap cap_net_admin,cap_net_raw=ep $(which dynamips)
```

### 2. Installasi VPCS

```bash
yay -S vpcs --noconfirm
```

### 3. Installasi IOL Untuk Simulasi Cisco

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
> Setelah perintah pertama lalu masukkan manual net.unix.max-dgram_qlen setelah itu EOL

### 4. Installasi uBridge

```bash
yay -S ubridge --noconfirm
```

### 5. Installasi Qemu

```bash
sudo pacman -S qemu
```

### 6. Installasi Docker

```bash
sudo pacman -S docker
```
Enable Docker service:

**SystemD:**

```bash
sudo systemctl enable docker.service && sudo systemctl restart docker.service
```

Installasi Untuk OpenRC

```bash
sudo pacman -S docker-openrc
```

**OpenRC**

```bash
rc-update add docker default && rc-service docker restart
```

Menambahkan user ke group docker:

```bash
sudo usermod -aG docker $USER
```

### 7. Installasi Wireshark

```bash
sudo pacman -S wireshark-qt
```
Menambahkan user ke group wireshark:

```bash
sudo usermod -aG wireshark $USER
```

### 8. Installasi GNS3 serta package yang dibutuhkan

```bash
sudo pacman -S qt5-svg qt5-websockets python-pip python-pyqt5 python-sip
```

**GNS3 GUI:**

```bash
yay -S gns3-gui --noconfirm
```

**GNS3 Server:**

```bash
yay -S gns3-server --noconfirm
```

Enable GNS3-Server :

```bash
systemctl enable gns3-server && systemctl start gns3-server
```

## Selesai

Selamat Mencoba !!

Mohon maaf jika ada kesalahan, jika masih bingung silahkan diskusi di komentar

##  Sumber & Referensi

* https://medium.com/@Ninja/install-gns3-on-arch-manjaro-linux-the-right-way-c5a3c4fa337d

