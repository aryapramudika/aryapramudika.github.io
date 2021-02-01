# Membuat Multi Bootable Di Flashdisk


## Persiapan

Untuk membuat multi bootable disini saya menggunakan software [Ventoy](https://www.ventoy.net/en/download.html)

yang perlu disiapkan adalah

1. Flashdisk
2. Laptop/PC
3. Iso OS seperti Windows/Linux

## Installasi & Konfigurasi Ventoy

Pertama kita download dulu menggunakan link diatas tadi.

![Ventoy](/img/ventoy-down.png 'Mendownload Ventoy')

Disini saya menggunakan ventoy versi linux

Extract file yang di download tadi lalu buka di terminal

![Ventoy1](/img/ventoy.png 'Buka Terminal')

Setelah itu cek flashdisk dengan perintah

```bash
sudo fdisk -l
``` 
![Ventoy2](/img/ventoy1.png 'Melihat nama flashdisk')

Setelah itu jalankan perintah

```bash
sudo ./Ventoy2Disk.sh -i /dev/sdc 
```
> Untuk PC/Laptop yang menggunakan GPT tambahkan **-g** sebelum /dev/sdc

jadi 

```bash
sudo ./Ventoy2Disk.sh -i -g /dev/sdc
```

![Ventoy3](/img/ventoy2.png 'Menjalankan perintah')

Perlu diperhatikan */dev/sdc* partisi flashdisk saya, mungkin bisa berbeda.

**You will install Ventoy to /dev/sdc

All the data on the disk /dev/sdc will be lost!!**

tekan **Y**

![Ventoy4](/img/ventoy3.png 'Tekan Y')

**Double-check. Continue? (y/n)**

Tekan **Y**

![Ventoy5](/img/ventoy4.png 'Tekan Y')


