# Membuat Multi Bootable Di Flashdisk


## Persiapan

Untuk membuat multi bootable disini saya menggunakan software [Ventoy](https://www.ventoy.net/en/download.html)

yang perlu disiapkan adalah

1. Flashdisk
2. Laptop/PC
3. Iso OS seperti Windows/Linux

## Installasi

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

Perlu diperhatikan */dev/sdc* adalah nama partisi flashdisk saya, di pc/laptop kalian mungkin berbeda.

**You will install Ventoy to /dev/sdc**

**All the data on the disk /dev/sdc will be lost!!**

tekan **Y**

![Ventoy4](/img/ventoy3.png 'Tekan Y')

**Double-check. Continue? (y/n)**

Tekan **Y**

![Ventoy5](/img/ventoy4.png 'Tekan Y')

Lalu tunggu sampai installasi selesai

![Ventoy6](/img/ventoy5.png 'Menunggu installasi selesai')

Installasi Selesai

![Ventoy7](/img/ventoy6.png 'Installasi Sukses')

## Penggunaan

Cara menggunakannya yaitu cukup mudah pertama buka direktori flashdisk yang sudah terinstall Ventoy

![Ventoy8](/img/ventoy7.png 'Buka direktori flashdisk')

Lalu copy/pindah file iso misal disini saya mengcopy file iso Debian Linux

![Ventoy9](/img/ventoy8.png 'Copy file iso')

Setelah itu tambahkan file iso lain misal Ubuntu

![Ventoy10](/img/ventoy9.png 'Menambahkan file iso ubuntu')

Dan berhasil lalu kita booting ke flashdisk

![VentoySukses](/img/ventoy-sukses.jpg 'Sukses membuat multi bootable')

## Keunggulan Ventoy dibanding Rufus/Multiboot

1. 100% Open-Source

2. Mudah digunakan

3. Cepat (hanya dibatasi oleh kecepatan menyalin file iso)

4. Dapat diinstal di USB / Disk Lokal / SSD / NVMe / Kartu SD.

5. Langsung boot dari file ISO / WIM / IMG / VHD (x) / EFI, tidak perlu mengekstrak file.

6. Tidak perlu terus menerus dalam disk untuk file ISO / IMG

7. Mendukung partisi MBR dan GPT (1.0.15+)

8. Mendukung x86 Legacy BIOS, IA32 UEFI, x86_64 UEFI, ARM64 UEFI

9. Mendukung UEFI Secure Boot (1.0.07+)

10. Penginstalan otomatis Windows didukung (1.0.09+)

11. RHEL7 / 8 / CentOS / 7/8 / SUSE / Ubuntu Server / Debian ... instalasi otomatis didukung (1.0.09+)

12. FAT32 / ExFAT / NTFS / UDF / XFS / Ext2 (3) (4) didukung untuk partisi utama

13. Mendukung file ISO yang lebih dari 4GB

14. Native boot untuk Legacy & UEFI

15. Sebagian besar jenis OS yang didukung, 610+ file iso teruji.

16. Mendukung boot Linux vDisk

17. Tidak hanya boot tetapi juga menyelesaikan proses instalasi

18. Menu dapat dialihkan secara dinamis antara mode List / TreeView

19. Konsep "Ventoy Compatible"

20. Kerangka Plugin

21. File injeksi ke lingkungan waktu proses

22. File konfigurasi boot pengganti secara dinamis

23. Tema dan menu yang sangat dapat disesuaikan

24. Dukungan proteksi penulisan drive USB

25. Penggunaan normal USB tidak terpengaruh

26. Data tidak rusak selama peningkatan versi

27. Tidak perlu memperbarui Ventoy ketika distro baru dirilis

## Selesai

Selamat Mencoba!

## Referensi

* https://github.com/ventoy/Ventoy

