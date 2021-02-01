# Installasi Windows 10 Di VMWare Workstation

## Sekilas tentang VMWare

VMware Workstation adalah sebuah perangkat lunak mesin virtual untuk arsitektur komputer x86 dan x86-64 dari VMware, sebuah bagian dari EMC Corporation. Perangkat lunak ini digunakan untuk membuat banyak x86 dan x86-64 komputer virtual dan digunakan secara simultan dengan sistem operasi yang digunakan. Setiap mesin virtual tersebut bisa menjalankan sistem operasi yang dipilih, seperti Windows, Linux, varian BSD dan lain sebagainya. Dalam arti yang sederhana, VMware workstation bisa menjalankan banyak sistem operasi secara simulatan dengan menggunakan satu fisik mesin. 

## Konfigurasi VM Windows 10

Pertama kita buka VMWare Workstationnya lalu klik **Create Virtual Machine**

![VMWareWindows](/img/vmware-windows.png 'Create Virtual Machine')

Setelah itu pada menu **Virtual Machine Configuration** kita pilih **Typical(recommended)**

![VMWareWindows1](/img/vmware-windows1.png 'Typical Recommended')

Selanjutnya di menu **Install Operating system from:** kita pilih **Use ISO image** dan masukkan ISO Windows 10

![VMWareWindows2](/img/vmware-windows2.png 'Pilih ISO')

![Memasukkan ISO Windows 10](/img/vmware-windows3.png 'Memasukkan ISO')

Pada menu **Guest Operating System** kita pilih **Microsoft Windows**

![VMWareWindows4](/img/vmware-windows4.png 'Pilih Microsoft Windows')

Selanjutnya di **Virtual Machine Name** biarkan default atau kita bisa custom direktori untuk penyimpanan file VM Windows 10

![VMWareWindows5](/img/vmware-windows5.png 'Konfigurasi Default')

Setelah itu kita mengatur **Disk Size** disini saya biarkan default yaitu 60 GB. Pilih **Store virtual disk as a single file** untuk membuat file VM hanya 1 file saja, jika ingin dibuat beberapa file maka pilih **Split virtual disk into multiple files** ini memudahkan ketika dilakukan pemindahan ke PC/Laptop lain karena filenya tidak terlalu besar.

![VMWareWindows6](/img/vmware-windows6.png 'Mengatur Disk Size')

Setelah itu kita klik Finish

![VMWareWindows7](/img/vmware-windows7.png 'Klik Finish')

> Sebelum finish kalian bisa custom manual seperti jumlah ram,jumlah cpu, dan network adapter di pilihan **Customize Hardware**

VM Windows 10 berhasil dibuat! selanjutnya kita ke tahap installasi Windows 10

## Installasi Windows 10 

Tidak ada perbedaan installasi Windows 10 di VMWare dan installasi Windows biasa, jadi jika kalian sudah bisa menginstall Windows 10 di PC/Laptop maka bisa melakukannya di VMWare.

Pertama memilih bahasa disini saya menggunakan bahasa **English(United States)** kalian bisa menggunakan bahasa lain seperti bahasa Indonesia. Konfigurasi lainnya saya biarkan default

![Win10](/img/windows10.png 'Pilih Bahasa')

Setelah itu kita klik **Install Now**

![Win10-1](/img/windows10-1.png 'Klik Install')

Selanjutnya masukkan product key jika punya, jika tidak kosongkan saja

![Win10-2](/img/windows10-2.png 'Masukkan Product Key')

Setelah itu pilih jenis Windows yang akan di install, disini saya memilih Windows 10 Pro

![Win10-3](/img/windows10-3.png 'Memilih jenis Windows')

Setujui semua license term

![Win10-4](/img/windows10-4.png 'Accept license term')

Pilih **Custom: Install Windows Only**

![Win10-5](/img/windows10-5.png 'Pilih Install Windows Only')

Lalu kita buat partisi, label **Primary** untuk C: dan **Logical** untuk partisi kedua misal D:

![Win10-6](/img/windows10-6.png 'Membuat Partisi')

Setelah itu kita tunggu 

![Win10-7](/img/windows10-7.png 'Menunggu')

Setelah sampai finishing up, maka akan restart ke windows secara otomatis

![Win10-8](/img/windows10-8.png 'Restart Otomatis')i

Selanjutnya pilih **Region Indonesia**

![Win10-9](/img/windows10-9.png 'Pilih Region Indonesia')

Lalu pilih Layout Keyboard **US**

![Win10-10](/img/windows10.png 'Pilih Layout Keyboard')

**Want to add second keyboard layout?** klik skip

![Win10-11](/img/windows10-11.png 'Klik Skip')

**How would you like to set up?** pilih **Set up for personal use**

![Win10-12](/img/windows10-12.png 'Pilih Setup for personal use')

Selanjutnya masukkan akun microsoft atau nama user 

![Win10-13](/img/windows10-13.png 'Masukkan Email/Nama')

Lalu masukkan password 

![Win-14](/img/windows10-14.png 'Masukkan Password')

lalu klik **Create PIN**

![Win10-15](/img/windows10-15.png 'Klik Create PIN')

Lalu buat PIN untuk login ke user 

![Win10-16](/img/windows10-16.png 'Buat PIN')

Klik **Accept**

![Accept](/img/windows10-17.png 'Klik Accept')

Klik **Yes**

![Klik Yes](/img/windows10-18.png 'Klik Yes')

Masukkan nomor telepon atau kosongkan, lalu klik **Next**

![Nomor Telepon](/img/windows10-19.png 'Masukkan Nomor Telepon atau Kosongkan')

**Back up your files  with OneDrive** kita pilih **Only save file to this PC**

![Only Save File to PC](/img/windows10-20.png 'Hanya save file ke PC')

Selanjutnya klik **No,thanks**

![No,Thanks](/img/windows10-21.png 'Klik No Thanks')

Tunggu sampai selesai dan berhasil

![Menunggu](/img/windows10-22.png 'Menunggu')

![Berhasil](/img/windows10-23.png 'Berhasil')

![Test Notepad](/img/windows10-24.png 'Test Notepad')

## Selesai

Selamat Mencoba !!

## Referensi

* https://id.wikipedia.org/wiki/VMware_Workstation

