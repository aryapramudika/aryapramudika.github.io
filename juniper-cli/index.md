# Basic Juniper CLI

## Konfigurasi Hostname

```Console
root@Juniper-R1# set system host-name Juniper-R2
root@Juniper-R1# commit 
root@Juniper-R2#
```

## Konfigurasi Root Password

```Console
root@Juniper-R2# set system root-authentication plain-text-password    
New password:
Retype new password:
root@Juniper-R2#
```

## Menambah user baru

```Console
root@Juniper-R2#set system login user pramudika class super-user authentication plain-text-password 
New password:
Retype new password:
root@Juniper-R2#
```


