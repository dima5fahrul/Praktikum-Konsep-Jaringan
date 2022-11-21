**Laporan Praktikum Konsep Jaringan Pekan 9**
> Nama  : Dimas Fahrul Putra Arismanto
>
> NRP   : 3121600005
>
> Kelas : 2 D4 IT A

# Praktikum Konsep Jaringan Project Kelas
### Topologi
![](https://i.postimg.cc/bJXTQD4G/Topologi.png)

Topologi di atas terdiri dari 10 Router. R1 sebagai router utama yang akan terhubung ke AS Number yang lain. Area R2 menggunakan routing protocol RIP, area R3 menggunakan OSPF, area R4 menggunakan Static Routing, sementara untuk menghubungkan area R2, R3, dan R4 menggunakan routing protocol BGP yang terhubung ke router pusat yakni R1.

### Detail konfigurasi setiap perangkat
**No**|**IP Address**|**CIDR**|**Network**|**Interface**|
:----:|:-------------:|:----------:|:----------------:|:---------:
|   R1    |   14.14.14.1    |  24  |   14.14.14.0    |  ether2   |
|         |   13.13.13.1    |  24  |   13.13.13.0    |  ether3   |
|         |   12.12.12.1    |  24  |   12.12.12.0    |  ether4   |
|   R2    |   12.12.12.2    |  24  |   12.12.12.0    |  ether1   |
|         |   27.27.27.2    |  24  |   27.27.27.0    |  ether2   |
|         |   28.28.28.2    |  24  |   28.28.28.0    |  ether3   |
|   R3    |   13.13.13.3    |  24  |   13.13.13.0    |  ether1   |
|         |   36.36.36.3    |  24  |   36.36.36.0    |  ether2   |
|         |   35.35.35.3    |  24  |   35.35.35.0    |  ether3   |
|   R4    |   14.14.14.4    |  24  |   14.14.14.0    |  ether1   |
|         |   41.41.41.4    |  24  |   41.41.41.0    |  ether2   |
|         |   49.49.49.4    |  24  |   49.49.49.0    |  ether3   |
|   R5    |   35.35.35.5    |  24  |   35.35.35.0    |  ether1   |
|         |   50.50.50.50   |  -   |   50.50.50.50   |    lo0    |
|   R6    |   36.36.36.6    |  24  |   36.36.36.0    |  ether1   |
|         |   60.60.60.60   |  -   |   60.60.60.60   |    lo0    |
|   R7    |   27.27.27.7    |  24  |   27.27.27.0    |  ether1   |
|         |   70.70.70.70   |  -   |   70.70.70.70   |    lo0    |
|   R8    |   28.28.28.8    |  24  |   28.28.28.0    |  ether1   |
|         |   80.80.80.80   |  -   |   80.80.80.80   |    lo0    |
|   R9    |   49.49.49.9    |  24  |   49.49.49.0    |  ether1   |
|         |   90.90.90.90   |  -   |   90.90.90.90   |    lo0    |
|   R10   |   41.41.41.10   |  24  |   41.41.41.0    |  ether1   |
|         | 100.100.100.100 |  -   | 100.100.100.100 |    lo0    |

### Ruang lingkup kerja

Dalam pratikum kali ini kelompok kami terdiri dari Dimas Fahrul Putra Arismanto (3121600005), Vanessa Florentina Patricia (3121600001), dan Feriand Dio (3121600009) bertugas untuk mengatur router R6 yng menggunakan routing OSPF sesuai area yang telah ditentukan. Kami melakukan konfigurasi routing tersebut dengan perintah sebagai berikut:

Tambah alamat addres untuk router R6 dan route ke R4 : 
> /interface bridge
> add name=lo0
> /ip address
> add address=36.36.36.6/24 interface=ether1 network=36.36.36.0
> add address=60.60.60.60 interface=lo0 network=60.60.60.60

Setting OSPF :
> /routing ospf area
> set [ find default=yes ] disabled=yes
> /routing ospf instance
> set [ find default=yes ] disabled=yes
> add name=lab-ospf router-id=6.6.6.6
> /routing ospf area
> add instance=lab-ospf name=backbone-lab
> /routing ospf network
> add area=backbone-lab network=36.36.36.0/24
> add area=backbone-lab network=60.60.60.60/32

### Table Routing
![](https://i.postimg.cc/nVdN8Tmp/Whats-App-Image-2022-11-20-at-17-48-18.jpg)
Terlihat dengan perintah ip route print untuk melihat isi tabel routing, bahwa router R6 sudah terhubung dengan router R3 dan R5 yang menggunakan routing protocol OSPF.

### Tes Koneksi
![](https://i.postimg.cc/rwgfWw9c/Whats-App-Image-2022-11-20-at-17-48-17-1.jpg)
![](https://i.postimg.cc/xjKyMd07/Whats-App-Image-2022-11-20-at-17-48-17.jpg)
![](https://i.postimg.cc/xT6m3JBs/Whats-App-Image-2022-11-20-at-17-48-18-1.jpg)

Gambar-gambar di atas merupakan test koneksi dengan perintah ping ke IP Address yang telah ditentukan.
