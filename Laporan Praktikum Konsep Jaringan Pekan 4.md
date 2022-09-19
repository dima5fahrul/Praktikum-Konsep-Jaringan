# Laporan Praktikum Konsep Jaringan Pekan 4
### Topologi
![](https://i.postimg.cc/2yRP6fkn/Screenshot-2022-09-17-145741.png)
Topologi diatas terdiri dari 2 router dan 2 PC client dengan subneting

### Konfigurasi IP Address PC3 dan PC4
![](https://i.postimg.cc/50gbZ0q6/Screenshot-2022-09-17-150251.png)
![](https://i.postimg.cc/Yq6KVjrk/Screenshot-2022-09-17-150437.png)

PC3
IP Address : 192.168.1.2
Subnet Mask : 255.255.255.0
Gateway : 192.168.1.1

PC4
IP Address : 192.168.3.3
Subnet Mask : 255.255.255.0
Gateway : 192.168.2.1

### Konfigurasi IP Address Router 6 dan Router 7
![](https://i.postimg.cc/wBGfQssh/Screenshot-2022-09-19-162656.png)
![](https://i.postimg.cc/zDsfPt1Q/Screenshot-2022-09-19-163109.png)
![](https://i.postimg.cc/zfFWJmq3/Screenshot-2022-09-19-163308.png)
![](https://i.postimg.cc/3J2XxfCM/Screenshot-2022-09-19-163352.png)

Router 6
GigabitEthernet 0/0/0
IP Address : 192.168.1.1
Subnet Mask : 255.255.255.0

GigabitEthernet 0/0/1
IP Address : 192.168.2.1
Subnet Mask : 255.255.255.0


Router 7
GigabitEthernet 0/0/0
IP Address : 192.168.3.2
Subnet Mask : 255.255.255.0

GigabitEthernet 0/0/1
IP Address : 192.168.2.2
Subnet Mask : 255.255.255.0

Untuk setting static routing di cisco packet tracer menggunakan periintah #ip route [Destination] [Subnet Mask] [Next Hop Address]

Keterangan:
ip route : Perintah membuat tabel routing static
Destination : Network jaringan yang dituju
Subnet Mask : Subnet mask jaringan yang dituju
Next Hop Address : Ip dari router yang akan dilewati

### Tes Ping
![](https://i.postimg.cc/65ncgp8N/Screenshot-2022-09-19-164553.png)
Tes ping PC3 ke PC4
![](https://i.postimg.cc/1XpWGm6P/Screenshot-2022-09-19-164752.png)
Tes ping PC4 ke PC3