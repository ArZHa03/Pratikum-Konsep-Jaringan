# Documentation Task Wireshark
## Colors Rule
Wireshark menggunakan warna untuk membantu mengidentifikasi jenis lalu lintas secara sekilas. Secara default, hijau adalah lalu lintas TCP, biru tua adalah lalu lintas DNS, biru muda adalah lalu lintas UDP, dan hitam mengidentifikasi paket TCP dengan masalah — misalnya, mereka bisa saja dikirim tidak sesuai pesanan.
| Color in Wireshark | Packet Type |
|:------------------:|:----------------------------------------------------------------------------:|
| Light purple | TCP |
| Light blue | UDP |
| Black | Packets with errors |
| Light green | HTTP traffic |
| Light yellow | Windows-specific traffic, including Server Message Blocks (SMB) and NetBIOS |
| Dark yellow | Routing |
| Dark gray | TCP SYN, FIN and ACK traffic |
| Red | Invalid Display Filter |

## Check IP Address | Default Gateway | Ping-it
[![IPR-Ping-Default-Gateway.png](https://i.postimg.cc/9Fr93YwM/IPR-Ping-Default-Gateway.png)](https://postimg.cc/RNxhKfR5)
Dapat kita ketahui bahwa ip pada laptop saya yakni 192.168.18.83 (enp4s0 / ethernet) dan default gatewaynya 192.168.18.1 dengan menggunakan ping pada default gateway yang diberikan oleh router (enp4s0 / ethernet) sudah bisa melakukan analisa suatu packet dengan bantuan Wireshark.

## Packet Analyzer
[![Packet-Analyzer.png](https://i.postimg.cc/GhVybTvj/Packet-Analyzer.png)](https://postimg.cc/CzC1N1PZ)
Gambar di atas menunjukkan bahwa IP Address pada adaptor enp4s0 / ethernet yakni 192.168.18.83 dan default gatewaynya 192.168.18.1 dengan data tersebut kita bisa mengetahui packet yang terlintas pada Wireshark.

### Detail Packet Analyzer Frame
[![Detail-Packet-Analyzer-Frame-Box.png](https://i.postimg.cc/hGbz8C6C/Detail-Packet-Analyzer-Frame-Box.png)](https://postimg.cc/FfzHNx9c)
Dalam box frame terdapat:
- Arrival Time: Sep  3, 2022 11:35:27.687452507 WIB
Menunjukkan waktu saat pengiriman data
- [Time delta from previous captured frame: 0.000000000 seconds]
[Time delta from previous displayed frame: 0.000000000 seconds]
[Time since reference or first frame: 0.000000000 seconds]
Menunjukkan waktu sebelum capture dari frame, yaitu 0.000000000 seconds, waktu setelah frame ditampilkan yaitu 0.000000000 seconds, dan waktu sejak awal frame 0.000000000 seconds.
- Frame Number: 1
Menunjukkan nomor dari frame tersebut yaitu 1.
- Frame Length: 98 bytes (784 bits)
Menunjukkan panjangnya frame adalah sebasar 98 bytes.
- [Protocols in frame: eth:ethertype:ip:icmp:data]
Menunjukkan protokol-protokol apa saja yang ada di frame 1 yaitu
ada Ethernet, Internet Protocol (IP), Internet Control Message Protocol
(ICMP) & Data.
- Kesimpulan:
Lapisan ini menunjukkan apa saja yang ada dalam satu frame yaitu seperti protokol-protokol yang ada di lapisan ini Ethernet, Internet Protocol (IP), Transmission Control Protocol (TCP), Hypertext Transfer Protocol (HTTP), dan data-text-lines.

### Detail Packet Analyzer Ethernet II
[![Detail-Packet-Analyzer-Ethernet.png](https://i.postimg.cc/mrG1HxXz/Detail-Packet-Analyzer-Ethernet.png)](https://postimg.cc/jDZSp1rt)
Dalam box Ethernet II terdapat:
- Source: QuantaCo_d3:f5:10 (d8:c4:97:d3:f5:10), Destination: HuaweiTe_02:6c:50 (c0:bc:9a:02:6c:50)
Menunjukkan MAC dari source yaitu QuantaCo_d3:f5:10 (d8:c4:97:d3:f5:10) dan MAC dari destination HuaweiTe_02:6c:50 (c0:bc:9a:02:6c:50).
- Kesimpulan:
Lapisan data link MAC dari source yaitu QuantaCo_d3:f5:10 (d8:c4:97:d3:f5:10) dan MAC dari HuaweiTe_02:6c:50 (c0:bc:9a:02:6c:50).

### Detail Packet Analyzer IPV4
[![Detail-Packet-Analyzer-IPV4.png](https://i.postimg.cc/dVCT3QBc/Detail-Packet-Analyzer-IPV4.png)](https://postimg.cc/bZzvFhWm)
Dalam box Internet Protocol terdapat:
- 0100 .... = Version: 4
Menunjukkan IP versi yang digunakan adalah versi 4
- .... 0101 = Header Length: 20 bytes (5)
Menunjukkan panjangnya header yang ada di lapisan network adalah sebesar 20 bytes
- InternetSrc: 192.168.18.83, Dst: 192.168.18.1
Menunjukkan IP dari source yaitu 192.168.18.52 dan IP dari destination
yaitu 192.168.18.1
- Kesimpulan:
Lapisan network, panjangnya header yang diberikan sebesar 20 bytes
dengan IP source 192.168.18.52 dan IP destination yaitu 192.168.18.1

### Detail Protcol ICMP
[![Detail-Packet-Analyzer-ICMP.png](https://i.postimg.cc/JnrypNWR/Detail-Packet-Analyzer-ICMP.png)](https://postimg.cc/XZP7JyJP)
- Type: 8 (Echo (ping) request)
- Code: 0
- Checksum: 0x6b53 [correct]
- Identifier (BE): 2 (0x0002)
- Identifier (LE): 512 (0x0200)
- Sequence Number (BE): 30 (0x001e)
- Sequence Number (LE): 7680 (0x1e00)
- [Response frame: 2]
Dari data ICMP di atas saat echo ping request tersebut, icmp bertype 8, code 0, dengan
algoritma checksum 0x6b53, banyak identifier (ident ifikasi) 512 bytes dan Sequence
number 7680 byte. Serta hasil diatas menunjukkan saat proses request ping, paket
dari source (192.168.18.52) IP address dari komputer kita akan merequest ({echo (ping)
request) ke destinat ion (192.168.18.1) IP address router wifi biznet.

