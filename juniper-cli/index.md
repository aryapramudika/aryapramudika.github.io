# Basic Juniper CLI

## Konfigurasi Hostname

```Console
[edit]
root@Juniper-R1# set system host-name Juniper-R2  

[edit]
root@Juniper-R1# commit 
commit complete

[edit]
root@Juniper-R2#```

## Konfigurasi Root Password

```Console
[edit]
root@Juniper-R2# set system root-authentication plain-text-password    
New password:
Retype new password:

[edit]
root@Juniper-R2# 
```

