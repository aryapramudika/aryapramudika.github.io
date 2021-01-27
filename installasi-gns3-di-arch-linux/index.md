# Installasi GNS3 Di Arch Linux Based


## Sekilas Tentang GNS3

GNS3 adalah simulator jaringan grafis yang memungkinkan anda untuk merancang topologi jaringan yang kompleks. Anda dapat menjalankan simulasi atau mengkonfigurasi perangkat mulai dari workstation sederhana hingga router yang powerfull seperti Cisco. Hal ini didasarkan pada Dynamips, Pemu/Qemu dan Dynagen.

## Persiapan

Pastikan sudah menginstall Yay AUR-Helper:

```bash
cd ~ && sudo pacman -Sy git && sudo pacman -S base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
Selanjutnya ke tahap Installasi

## Installasi & Konfigurasi

Untuk installasi kita perlu menginstall package satu persatu

### 1. Dynamips

```bash
sudo pacman -S libelf libpcap cmake && yay -S dynamips --noconfirm && sudo setcap cap_net_admin,cap_net_raw=ep $(which dynamips)
```

### 2. VPCS

```bash
yay -S vpcs --noconfirm
```

### 3. IOL Untuk Simulasi Cisco

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
Lalu masukkan
net.unix.max_dgram_qlen=10000
dan tutup dengan perintah
EOL
```
### 4. uBridge

```bash
yay -S ubridge --noconfirm
```

### 5. Qemu

```bash
sudo pacman -S qemu
```

### 6. Docker

```bash
sudo pacman -S docker
```
Enable Docker service:

**SystemD:**

```bash
sudo systemctl enable docker.service
sudo systemctl start docker.service
```
dengan menggunakan perintah systemctl *enable* docker otomatis akan aktif setelah booting, jika ingin mengaktifkan docker ketika dibutuhkan saja maka gunakan perintah systemctl *start*   

**OpenRC**

```bash
sudo pacman -S docker-openrc
```

```bash
rc-update add docker default
rc-service docker restart
```
Untuk init sistem lain silahkan disesuaikan.

Menambahkan user ke group docker:

```bash
sudo usermod -aG docker $USER
```

### 7. Wireshark

```bash
sudo pacman -S wireshark-qt
```
Menambahkan user ke group wireshark:

```bash
sudo usermod -aG wireshark $USER
```

### 8. GNS3

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

Menjalankan GNS3-Server :

```bash
systemctl enable gns3-server
systemctl start gns3-server
```

## Selesai

Selamat Mencoba !!

Mohon maaf jika ada kesalahan, jika masih bingung silahkan diskusi di komentar

##  Sumber & Referensi

* https://medium.com/@Ninja/install-gns3-on-arch-manjaro-linux-the-right-way-c5a3c4fa337d

* https://lms.onnocenter.or.id/wiki/index.php/Gns3

* https://bandithijo.github.io/blog/gns3-arch-linux

