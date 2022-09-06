# Laporan Praktikum Konsep Jaringan
#### Pewarnaan Paket

| Color | Packet Type |
| ------ | ------ |
| Light Purple | TCP |
| Light Blue | UDP |
| Black | Packet with Errors |
| Light Green | HTTP traffic |
| Light Yellow | Windows-specific traffic, including Server Message Blocks (SMB) and NetBIOS |
| Dark Yellow | Routing |
| Dark Grey | TCP SYN, FIN and ACK traffic |

![](https://www.wireshark.org/docs/wsug_html_chunked/wsug_graphics/ws-coloring-rules-dialog.png)

#### Cek IP Address
![](https://i.ibb.co/yFkkR55/Screenshot-2022-09-06-064024.png)
Dapat kita ketahui bahwa ip pada laptop saya yakni 192.168.1.14 dan default gatewaynya 192.168.1.8 dengan menggunakan ping pada default gateway yang diberikan oleh router (enp4s0 / ethernet) sudah bisa melakukan analisa suatu packet dengan bantuan Wireshark.

#### Detail Packet Analyzer Frame
![](https://i.ibb.co/tzK3RsR/Screenshot-2022-09-06-064528.png)
Dalam box frame terdapat:
 - Arrival Time: Sep  6, 2022 06:39:11.473496000 SE Asia Standard Time Menunjukkan waktu saat pengiriman data
 - [Time delta from previous captured frame: 0.005577000 seconds] [Time delta from previous displayed frame: 0.005577000 seconds] [Time since reference or first frame: 71.282075000 seconds] Menunjukkan waktu sebelum capture dari frame, yaitu 0.005577000 seconds, waktu setelah frame ditampilkan yaitu 0.005577000 seconds, dan waktu sejak awal frame 71.282075000 seconds.
 - Frame Number: 60 Menunjukkan nomor dari frame tersebut yaitu 919.
 - Frame Length: 74 bytes (592 bits) Menunjukkan panjangnya frame adalah sebasar 1312 bits.
 - [Protocols in frame: eth:ethertype:ip:icmp:data] Menunjukkan protokol-protokol apa saja yang ada di frame 1 yaitu ada Ethernet, Internet Protocol (IP), Internet Control Message Protocol (ICMP) & Data.
 - Kesimpulan: Lapisan ini menunjukkan apa saja yang ada dalam satu frame yaitu seperti protokol-protokol yang ada di lapisan ini Ethernet, Internet Protocol (IP), Transmission Control Protocol (TCP), Hypertext Transfer Protocol (HTTP), dan data-text-lines.
 
 
#### Detail Packet Analyzer Ethernet II
![](https://i.ibb.co/CKV76PZ/image.png)
Source: SamsungE_1f:c8:30 (0c:a8:a7:1f:c8:30), Destination: 82:30:5b:ed:9d:48 (82:30:5b:ed:9d:48) menunjukkan MAC dari source yaitu SamsungE_1f:c8:30 (0c:a8:a7:1f:c8:30) dan MAC dari destination 82:30:5b:ed:9d:48 (82:30:5b:ed:9d:48)


#### Detail Packet Analyzer IPV4
![](https://i.ibb.co/nMHvNP0/image.png)
- 0100 .... = Version: 4 Menunjukkan IP versi yang digunakan adalah versi 4 .... 0101 = Header Length: 20 bytes (5) Menunjukkan panjangnya header yang ada di lapisan network adalah sebesar 20 bytes
- Source Address: 192.168.1.8, Destination Address: 192.168.1.14 Menunjukkan IP dari source yaitu 192.168.1.8 dan IP dari destination yaitu 192.168.1.14
- Kesimpulan: Lapisan network, panjangnya header yang diberikan sebesar 20 bytes dengan IP source 192.168.1.8 dan IP destination yaitu 192.168.1.14


#### Protocol TCP
![](https://i.ibb.co/W28cw70/image.png)
