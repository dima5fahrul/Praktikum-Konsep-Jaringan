**Laporan Praktikum Konsep Jaringan Pekan 9**
> Nama  : Dimas Fahrul Putra Arismanto
>
> NRP   : 3121600005
>
> Kelas : 2 D4 IT A

# Dynamic Routing

#### Apa itu dynamic routing?
Dynamic Routing atau yang biasa disebut dengan routing dinamis adalah metode routing yang me-rutekan jalur secara otomatis dengan tabel routingnya sendiri. Dynamic routing akan selalu update/memperbaharui jika sewaktu-waktu ada perubahan topologi pada jaringan. Ini merupakan keuntungan tersendiri menggunakan dynamic routing.

Berbicara masalah static routing, routing jenis ini jauh lebih rumit dibandingkan dengan dynamic routing. Apalagi tabel routing yang serba manual, ini bisa menyebabkan kita sakit kepala, terlebih lagi jika ada perubahan topologi ataupun alamat jaringan.

Nah kembali lagi ke dynamic routing, beberapa contoh dynamic routing yang sering digunakan oleh perusahaan untuk jaringan internalnya yaitu RIP, IGRP, OSPF, dan EIGRP. Masing-masing jenis router tersebut memiliki kelebihan dan kekurangan masing-masing, sehingga membutuhkan kejelian yang tinggi serta pertimbangan yang matang saat memilih jenis router tersebut.

Kita juga harus bisa menyesuaikan kebutuhan dan kemampuan perusahaan yang sedang membutuhkan jaringan tersebut, tujuannya tidak lain yaitu agar tidak ada kesalahan teknis, baik pertimbangan untuk pengembangan jaringan di masa mendatang maupun dari segi finansial/biaya.

#### Kelebihan dan kekurangan
Kelebihan Dynamic Routing
- Administrator tidak turut campur tangan
- Hanya mengenalkan alamat/address yang terhubung langsung dengan perangkat router tersebut
- Jika terjadi penambahan suatu network/jaringan baru, maka semua router tidak perlu dikonfigurasi ulang, tetapi hanya perlu mengkonfigurasi router yang berkaitan saja
- Router akan secara otomatis berbagi informasi
- Routing table dibuat secara dinamik/berubah-ubah
- Sangat cocok diterapkan untuk jaringan atau area yang relatif luas/besar
- Tidak perlu mencari tahu semua alamat network yang ada pada jaringan tersebut

Kekurangan Dynamic Routing
- Beban kerja perangkat router menjadi lebih berat karena selalu memperbarui IP Table pada setiap waktu tertentu
- Kecepatan pengenalan dan kelengkapan IP Table terhitung lama karena perangkat router membroadcast ke semua router lain sampai ada yang cocok. Akibatnya yaitu kita harus menunggu beberapa saat setelah melakukan konfigurasi agar setiap router mendapat semua alamat IP yang ada.

Jika dibandingkan antara kelebihan dan kekurangannya tentu saja lebih banyak keuntungan yang didapatkan. Inilah mengapa dynamic routing menjadi pilihan banyak orang walaupun ada saja kekurangannya, namun tidak menutup kemungkinan orang-orang akan tetap memlih dynamic routing dibanding static routing.

#### Apa itu RIP?
Karakteristik dari RIP (Routing Infotmation Protocol) antara lain :

- Menggunakan algoritma Distance Vector (routing by rumor)
- Menggunakan Protokol Routing Distance Vector
- Metric berdasarkan hop count untuk pemilihan jalur yang terbaik
- Jika hop count lebih dari 15, maka paket akan dibuang
- Update routing akan dilaksanakan secara broadcast setiap 30 detik

RIP atau yang biasa disebut Routing Information Protocol merupakan routing protokol yang memberikan routing table berdasarkan router yang terhubung langsung, Selanjutnya router akan memberikan informasi ke router selanjutnya yang terhubung langsung dengan jaringan tersebut. Adapun informasi yang dibagikan oleh RIP yaitu : Host, Network, Subnet dan Rute default.

RIP sendiri terbagi menjadi dua bagian, yaitu :

**RIPv1 / RIP versi 1**

Karakteristik dari RIPv1 antara lain :

- Hanya mendukung routing classfull
- Perbaikan routing broadcast
- Tak ada info subnet yang dimasukkan dalam perbaikan routing
- Tidak mendukung VLSM (Variabel Length Subnet Mask)

**RIPv2 / RIP versi 2**

Karakteristik dari RIPv2 antara lain :

- Info subnet dimasukkan dalam perbaikan routing
- Mendukung routing classfull dan routing classless
- Mendukung VLSM (Variabel Length Subnet Mask)
- Perbaikan routing multicast

Secara umum protokol RIPv1 memang tidak jauh berbeda dengan protokol RIPv2. Perbedaan yang terlihat secara langsung yaitu pada informasi yang dibagikan. Pada protokol RIPv2 informasi yang dibagikan yaitu terdapat autenfikasi didalamnya.

**Persamaan antara RIP v1 dengan RIP  v2 :**

- Menggunakan Distance Vector Routing Protocol
- Metric berupa hop count
- Maksimal hop count 15
- Sama-sama menggunakan port 520
- Menjalankan auto summary secara default

**Perbedaan protokol RIP v2 dibanding protokol RIP v1 :**

- Bersifat classless routing protocol. Artinya yaitu menyertakan field SM dalam paket update yang dikirimkan sehingga RIP v.2 mendukung VLSM & CIDR
- Mengirimkan paket update dan menampung paket update versi 2
- Mengirimkan update ke address/alamat multicast yaitu 224.0.0.9
- Pada RIPv2, Auto Summary dapat dimatikan
- Mendukung fungsi keamanan berupa authentication. Hal ini dapat mencegah routing update dikirim atau diterima dari sumber yang mencurigakan.

> Referensi : https://www.webmobile.id/pengertian-dynamic-routing/#Pengertian_Dynamic_Routing_Routing_Dinamis

# Konfigurasi Dynamic Routing menggunakan RIP

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
**Device Name**|**Destination Network**
:----:|:-------------:|
Router9|192.168.4.0|
||192.168.3.0|
||192.168.2.0|
Router10|192.168.5.0|
||192.168.3.0|
||192.168.1.0|
Router8|192.168.2.0|
||192.168.1.0|

Dalam konfigurasi static routing diatas, dapat dilakukan dengan cara memasukkan perintah pada CLI. Struktur perintah untuk memberikan konfigurasi di atas sebagai berikut:

        Router(config)#router rip
        Router(config-router)#network [Destination Network]

#### Konvergensi dan Testing
**PC0 ke PC1**
![](https://i.postimg.cc/ZKjK7TYG/Screenshot-2022-10-13-184824.png)
**PC1 ke PC0**
![](https://i.postimg.cc/rFTNG9zh/Screenshot-2022-10-13-185117.png)

Konvergensi adalah keadaan satu set router yang memiliki informasi topologi yang sama tentang internetwork di mana mereka beroperasi. Untuk satu set router telah konvergen , mereka harus telah mengumpulkan semua informasi topologi yang tersedia dari satu sama lain melalui protokol routing yang diimplementasikan , informasi yang mereka kumpulkan tidak boleh bertentangan dengan informasi topologi router lain di set, dan itu harus mencerminkan keadaan sebenarnya dari jaringan. Dengan kata lain: dalam jaringan konvergensi semua router "setuju" seperti apa topologi jaringan itu.

Konvergensi merupakan gagasan penting untuk satu set router yang terlibat dalam routing dinamis . Semua Protokol Gateway Interior mengandalkan konvergensi agar berfungsi dengan baik. Untuk konvergen itu adalah keadaan normal dari sistem otonom operasional . Exterior Gateway Routing Protocol BGP biasanya tidak pernah konvergen karena Internet terlalu besar untuk perubahan yang dapat dikomunikasikan dengan cukup cepat.

Terlihat pada percobaan di atas bahwa paket yang dikirimkan dari PC0 ke PC1 adalah sebagai berikut:

1. PC0 mengirimkan paket ke router 9.
2. Router 10 menerima paket dan mengirimkan paket ke router 9.
3. Router 10 menerima paket dan mengirimkan paket ke PC1.
4. PC1 menerima paket.

Tracert di atas ialah percobaan yang pertama kali jadi belum ada routing table yang ada di router 10. Routing table akan terupdate setelah router 2 menerima routing table dari router 9. Terdapat jeda waktu disana karena routing table belum terupdate maka dari itu sistem convergent di mulai pada saat routing table masih belum terbentuk.













