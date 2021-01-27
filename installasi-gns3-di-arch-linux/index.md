# Installasi GNS3 Di Arch Linux Based


## Latar Belakang

Karena saya belum menemukan artikel cara installasi gns3 arch linux versi bahasa Indonesia, jadi saya membuatnya sendiri

## Tujuan

Agar memudahkan pengguna distro Arch Based dalam melakukan Installasi GNS3


## Sekilas Tentang gns3

GNS3 (Graphic Network Simulator) adalah software simulasi jaringan komputer berbasis GUI yang mirip dengan Cisco Packet Tracer. Namun pada GNS3 memungkinkan simulasi jaringan yang komplek, karena menggunakan operating system asli dari perangkat jaringan seperti cisco dan juniper. Sehingga kita berada kondisi lebih nyata dalam mengkonfigurasi router langsung daripada di Cisco Packet Tracer. GNS3 adalah alat pelengkap yang sangat baik untuk laboratorium nyata bagi network engineer, administrator dan orang-orang yang ingin belajar untuk sertifikasi seperti Cisco CCNA, CCNP, CCIP dan CCIE serta Juniper JNCIA, JNCIS dan JNCIE.

## Persiapan

Pastikan sudah menginstall Yay AUR-Helper:

```bash
cd ~ && sudo pacman -Sy git && sudo pacman -S base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
Selanjutnya ke tahap Installasi

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
> Setelah perintah pertama lalu masukkan manual net.unix.max_dgram_qlen=10000 setelah itu EOL

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

### 8. Installasi GNS3 Serta Package Yang Dibutuhkan

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

* https://kelasinong.blogspot.com/2019/10/c.html

