# Laporan Praktikum Konsep Jaringan Pekan 5
## Konfigurasi Inter VLAN Routing
### Topologi
![](https://i.postimg.cc/xCQ5c5SD/Screenshot-2022-09-24-114256.png)
Topologi di atas terdiri dari 1 router, 1 switch, dan 2 PC client dengan subneting

### Konfigurasi IP Address PC0 dan PC1
![](https://i.postimg.cc/kMhmt1Td/Screenshot-2022-09-24-115731.png)
![](https://i.postimg.cc/Xv8MNQrm/Screenshot-2022-09-24-115849.png)

PC0
IP Address : 172.17.10.21
Subnet Mask : 255.255.0.0

PC1
IP Address : 192.168.30.23
Subnet Mask : 255.255.0.0

### Konfigurasi Switch VLAN
![](https://i.postimg.cc/MKPmwRZ5/Screenshot-2022-09-24-120902.png)

Konfigurasi VLAN pada Switch yang dimana PC0 adalah grup VLAN 10 dan PC3 VLAN 30

### Konfigurasi Router
![](https://i.postimg.cc/XYNHn40K/Screenshot-2022-09-24-121525.png)
![](https://i.postimg.cc/Znzdx68P/Screenshot-2022-09-25-142611.png)
Jika kita cek dengan #show ip route dan ip yang tersambung sudah terconnected, maka pembuatan vlan berhasil

### Tes Ping
![](https://i.postimg.cc/26QpVf2k/Screenshot-2022-09-25-142409.png)
Tes ping PC0 ke PC1
![](https://i.postimg.cc/fRDvNQ07/Screenshot-2022-09-25-142825.png)
Tes ping PC1 ke PC0

## Konvigurasi router-on-a-stick inter VLAN routing

### Topologi
![](https://i.postimg.cc/VNTG1HwY/Screenshot-2022-09-25-143400.png)
Topologi di atas terdiri dari 2 PC, 1 Switch, dan 1 Router

### Konfigurasi IP Address PC3 dan PC4 
![](https://i.postimg.cc/bJWKCwr9/Screenshot-2022-09-25-143314.png)
![](https://i.postimg.cc/cHhvwPJW/Screenshot-2022-09-25-143703.png)
PC0
IP Address : 172.17.10.21
Subnet Mask : 255.255.0.0

PC1
IP Address : 192.168.30.23
Subnet Mask : 255.255.0.0

### Konfigurasi Router
![](https://i.postimg.cc/XqT4Cg93/Screenshot-2022-09-25-143905.png)