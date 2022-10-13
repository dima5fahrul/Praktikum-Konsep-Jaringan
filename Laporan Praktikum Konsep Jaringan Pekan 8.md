**Laporan Praktikum Konsep Jaringan Pekan 8**
> Nama  : Dimas Fahrul Putra Arismanto
> NRP   : 3121600005
> Kelas : 2 D4 IT A

# Traceroute dan Time to Live

#### Apa itu Time to Live?
Time to Live (TTL) adalah mekanisme yang membatasi periode waktu sebuah paket data dalam komputer atau jaringan. TTL dapat diimplementasikan sebagai counter atau timestamp yang terdapat dalam data.

Setelah perhitungan atau jangka waktu telah berlalu, data akan dibuang. Dalam jaringan komputer, TTL mencegah paket data yang masuk secara terus menerus (tanpa batas). Dalam penerapannya, TTL digunakan untuk meningkatkan kinerja caching atau meningkatkan privasi.

#### Cara kerjanya bagaimana?
TTL dapat kamu temukan ketika melakukan ping pada suatu website menggunakan command line seperti CMD. Fungsinya, untuk membatasi waktu dalam ping dalam jangka waktu tertentu.

Jika dalam satu program ping TTL bernilai 50, maka dalam batawan waktu tertentu hingga waktu TTL semakin berkurang dan juga paket data telah melewati banyak router, maka makin lama TTL akan habis atau expired. TTL sengaja dibatasi agar tidak terjadi perputaran jaringan atau circular routing.

Semakin besar nilai latency atau ping, maka komunikasi internet semakin buruk atau melambat.

![](https://i.postimg.cc/qMhMwLrV/Screenshot-2022-10-13-174722.png)
> Referensi : https://caraguna.com/apa-itu-time-to-live/#:~:text=Time%20to%20Live%20%28TTL%29%20adalah%20mekanisme%20yang%20membatasi,atau%20jangka%20waktu%20telah%20berlalu%2C%20data%20akan%20dibuang.

#### Kalau Traceroute?
Traceroute adalah metode diagnostik jaringan yang mana suatu paket dikirim ke suatu tujuan. Software traceroute melaporkan lokasi dan waktu tempuh setiap lompatan paket saat bepergian dari satu perangkat ke perangkat lain di jaringan perantara.

Contoh program yang menjalankan traceroute Adalah tracert command di Microsoft Windows atau traceroute command di Linux, macOS, dan BSD.

#### Bagaimana Traceroute Bekerja
Traceroute asli adalah utilitas UNIX tetapi hampir semua platform memiliki sesuatu yang serupa. Windows menyertakan utilitas traceroute yang disebut tracert. Di Windows, Anda dapat menjalankan tracert dengan memilih Start => Run…, dan memasukkan tracert diikuti dengan nama domain dari host. Sebagai contoh:

tracert www.pcwebopedia.com

Utilitas Traceroute bekerja dengan mengirimkan paket dengan low time-to-live (TTL) fields. Nilai TTL menentukan berapa banyak hop paket diizinkan sebelum dikembalikan. Ketika sebuah paket tidak dapat mencapai tujuannya karena nilai TTL terlalu rendah, host terakhir mengembalikan paket, dan mengidentifikasi dirinya. Dengan mengirimkan serangkaian paket dan menambah nilai TTL dengan setiap paket berturut-turut, traceroute mengetahui siapa semua host perantara.

> Referensi : https://www.jetorbit.com/blog/apa-itu-traceroute/#traceroute-adalah

# Konfigurasi Tracerouting

#### Topologi
![](https://i.postimg.cc/286030WW/Screenshot-2022-10-13-170034.png)


#### Detail konfigurasi setiap perangkat
**No**|**Device Name**|**Interface**|**IP Add/Netmask**|**Gateway**
:----:|:-------------:|:----------:|:----------------:|:---------:
1|Router9|gig0/0|192.168.2.1/24
 |||gig0/1|192.168.3.1/24
 |||gig0/2|192.168.4.1/24
||Router10|gig0/0|192.168.1.1/24
|||gig0/1|192.168.3.2/24
|||gig0/2|192.168.5.1/24
||Router8|gig0/0|192.168.2.2/24
|||gig0/1|192.168.1.2/24
||||
2|Switch0||192.168.4.0/24
||Switch1||192.168.5.0/24
||||
3|PC0|Fa0|192.168.4.2/24|192.168.4.1
||PC1|Fa0|192.168.5.2/24|192.168.5.1

#### Detail konfigurasi static route pada router
**Device Name**|**Destination Network**|**Netmask**|**Via**|**Matric**
:----:|:-------------:|:----------:|:----------------:|:---------:
Router9|192.168.5.0|255.255.255.0|192.168.3.2|10(Default)
||192.168.1.0|255.255.255.0|192.168.2.2|10(Default)
Router10|192.168.4.0|255.255.255.0|192.168.3.1|10(Default)
||192.168.2.0|255.255.255.0|192.168.1.2|10(Default)
Router8|192.168.4.0|255.255.255.0|192.168.2.1|10(Default)
||192.168.5.0|255.255.255.0|192.168.1.1|10(Default)

Dalam konfigurasi static routing diatas, dapat dilakukan dengan cara memasukkan perintah pada CLI. Struktur perintah untuk memberikan konfigurasi di atas sebagai berikut:
"ip route [destination network] [netmask] [via] [metric]".

#### Percobaan Traceroute
**PC0 ke PC1**
![](https://i.postimg.cc/ZKjK7TYG/Screenshot-2022-10-13-184824.png)
**PC1 ke PC0**
![](https://i.postimg.cc/rFTNG9zh/Screenshot-2022-10-13-185117.png)

Traceroute ini diawali dengan PC lalu ke switch dan ke router. Pada kondisi ini tidak melewati Router8 karena masing - masing router memiliki matric default sehingga komunikasi mengambil jalan tercepat. Jika ingin melewati Router8, maka harus mengurangi jumlah matric pada router tersebut.

**Device Name**|**Destination Network**|**Netmask**|**Via**|**Matric**
:----:|:-------------:|:----------:|:----------------:|:---------:
Router9|192.168.5.0|255.255.255.0|192.168.3.2|10(Default)
||192.168.5.0|255.255.255.0|192.168.2.2|1
Router10|192.168.4.0|255.255.255.0|192.168.3.1|10(Default)
||192.168.4.0|255.255.255.0|192.168.1.2|1
Router8|192.168.4.0|255.255.255.0|192.168.2.1|10(Default)
||192.168.5.0|255.255.255.0|192.168.1.1|10(Default)

**PC0 ke PC1**
![](https://i.postimg.cc/251dGkvG/Screenshot-2022-10-13-193229.png)
**PC1 ke PC0**
![](https://i.postimg.cc/XJcrcm2x/Screenshot-2022-10-13-193351.png)

Terlihat pada traceroute di atas, terdapat 4 ip yang dilewati karena tertambah dengan Router8 dengan matric yang berjumlah 1 sehingga matric yang berjumlah lebih sedikit akan diprioritaskan terlebih dahulu














