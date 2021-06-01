# Basic Juniper CLI



## Candidate & Active Configuration

### Candidate
Candidate konfigurasi adalah konfigurasi yang kita lakukan sebelum commit

```Shell
root@Juniper-R2# show
```

### Active
Active konfigurasi adalah konfigurasi yang sedang berjalan atau setelah di commit

```Shell
root@Juniper-R2#run show configuration
```
## Konfigurasi Hostname

```Shell
root@Juniper-R1# set system host-name Juniper-R2
root@Juniper-R1# commit 
root@Juniper-R2#
```

## Konfigurasi Root Password

```Shell
root@Juniper-R2# set system root-authentication plain-text-password    
New password:
Retype new password:
root@Juniper-R2#
```

## Manajemen User

### Menambah User Baru

```Shell
root@Juniper-R2#set system login user pramudika class super-user authentication plain-text-password 
New password:
Retype new password:
root@Juniper-R2#
```
### Menghapus User Baru
```Shell
root@Juniper-R2# delete system login user pramudika 
root@Juniper-R2# commit 
commit complete
```

## Commit

### Commit biasa
```Shell
root@Juniper-R2#commit
```

### Commit dengan Komentar

```Shell
root@Juniper-R2#commit comment "Menambahkan IP di em2"
```

### Commit di jam tertentu

```Shell
root@Juniper-R2#commit at "2021-01-01 19:02:00"
```

### Commit check(Mengecek konfigurasi sudah benar atau ada yang salah)

```Shell
root@Juniper-R2# commit check 
configuration check succeeds
```

### Commit&Quit

```Shell
root@Juniper-R2# commit and-quit 
commit complete
Exiting configuration mode

root@Juniper-R2> 
```
### Rollback

Mengembalikan konfigurasi awal sebelum di commit, nomor commit bisa dilihat di **run show system commit**

```Shell
rollback 1
commit
```

## Konfigurasi Waktu 

Melihat waktu

```Shell
run show system uptime
```

### Konfigurasi Zona Waktu
```Shell
root@Juniper-R2# set system time-zone Asia/Jakarta 
root@Juniper-R2# commit
```
 
### Manual
```Shell
root@Juniper-R2# run set date "202106011915.00" 
Tue Jun  1 19:15:00 WIT 2021
```
### NTP Server
Dengan Alamat NTP id.pool.ntp.org
```Shell
root@Juniper-R2# set system ntp server 162.159.200.1 
root@Juniper-R2# commit 
```



