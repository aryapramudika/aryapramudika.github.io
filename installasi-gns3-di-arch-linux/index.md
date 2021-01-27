# Installasi GNS3 Di Arch Linux Based


## Sekilas Tentang GNS3

GNS3 adalah simulator jaringan grafis yang memungkinkan digunakan untuk merancang topologi jaringan yang kompleks. GNS3 dapat menjalankan simulasi atau mengkonfigurasi perangkat mulai dari workstation sederhana hingga router yang powerfull seperti Cisco.

## Persiapan

Pastikan sudah menginstall Yay AUR-Helper:

```bash
cd ~ && sudo pacman -Sy git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
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

![lib32](/img/lib32.png 'Mengaktifkan Repository 32 Bit')

```bash
sudo pacman -Sy lib32-openssl lib32-gcc-libs && sudo ln -s /usr/lib32/libcrypto.so.1.0.0 /usr/lib32/libcrypto.so.4
```
Mencegah jika nanti terjadi error di EXCESSCOLL

```bash
sudo sysctl net.unix.max_dgram_qlen=10000
```
Konfigurasi Permanen

```bash
sudo echo "net.unix.max_dgram_qlen=10000" > /etc/sysctl.d/99-sysctl.conf
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

> Setelah konfigurasi Docker dan Wireshark pastikan kita **Logout** dan **Login** kembali agar user kita berhasil ditambahkan ke dalam docker & wireshark group

Setelah Logout dan Login pastikan dengan perintah ini.

```bash
id -Gn
```
Output perintah:

> user wireshark docker libvirt video wheel

Perhatikan pada output terdapat tambahan **wireshark** dan **docker**

### 8. GNS3

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
Untuk init sistem lain seperti OpenRC yang saya gunakan, gns3-server akan aktif sendiri ketika kita menjalankan GNS3

## Membuat Launcher GNS3

Jika launcher GNS3 belum muncul di Desktop Environment setelah installasi, maka buat launcher secara manual

```bash
sudo tee -a /usr/share/applications/gns3.desktop > /dev/null << EOL
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=GNS3
Comment=Graphical Network Simulator 3
Exec=/usr/bin/gns3
Icon=gns3
Terminal=false
Categories=Application;Network;Qt;
EOL
```

## Selesai

Selamat Mencoba !!

Mohon maaf jika ada kesalahan, jika masih bingung silahkan diskusi di komentar

##  Sumber & Referensi

* https://medium.com/@Ninja/install-gns3-on-arch-manjaro-linux-the-right-way-c5a3c4fa337d

* https://lms.onnocenter.or.id/wiki/index.php/Gns3

* https://bandithijo.github.io/blog/gns3-arch-linux

