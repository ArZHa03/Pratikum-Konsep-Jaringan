# Documentation Task Packet-Tracer
## Topologi
[![Topologi.png](https://i.postimg.cc/VsZh1Mb0/Topologi.png)](https://postimg.cc/G9YKx4Kb)
Topologi di atas terdiri dari 3 pc client dan 1 hub dengan subneting 192.168.1.1 - 192.168.1.3 dengan icdr 24 tanpa default gateway dan dns karena tanpa router serta tidak dihubungkan ke jaringan internet.

### Ping PC0 to PC1 (First Time) | Check ARP Cache | Scenario 1
[![Scenario1.png](https://i.postimg.cc/5NZkQVgx/Scenario1.png)](https://postimg.cc/xc3PBBB7)
Terlihat sebelum melakukan ping tidak ada ARP cache yang terdaftar dan setelah melakukan ping pada PC0 (192.168.1.1) ke PC1 (192.168.1.2) terlihat Arp cache pada PC0 memiliki informasi IP / Logikal Address PC1 (192.168.1.2) dengan Physical Address / MAC Address yaitu 00e0.8f19.b738.
Sebenarnya ketika proses ping dari PC0 (192.168.1.1) ke PC1 (192.168.1.2), proses terssebut ditahan atau ditunda terlebih dahulu karena pada layer Data Link (OSI Layer - 2) belum ditemukannya MAC Address sebelum packet request (ping) dikirimkan dan untuk mencari MAC Address tersebut diperlukan Paket Broadcast dengan Broadcast Address yaitu FFFF.FFFF.FFFF.
[![Request-Packet-Broadcast.png](https://i.postimg.cc/MKcFGTyP/Request-Packet-Broadcast.png)](https://postimg.cc/gnWDSGt8)
Broadcast itu sendiri adalah proses mengirimkan sebuah paket kepada semua device yang terhubung dalam satu area jaringan subneting dari device yang mengirimnya.
[![Replay-Packet-Broadcast.png](https://i.postimg.cc/VN9TcVjz/Replay-Packet-Broadcast.png)](https://postimg.cc/Y49868nP)
Setelah paket broadcast tersebut diterima ke semua device dalam satu jaringan maka IP yang sesuai (192.168.1.2) akan melakukan replay sementara yang IP nya tidak sesuai tidak akan melakukan replay dan akan melakukan drop pada paket tersebut yang terjadi pada Layer Network (OSI Layer - 3).


### Ping PC0 ke PC1 (Second Time) | Check ARP Cache | Scenario 2
[![Scenario2.png](https://i.postimg.cc/Fz6CZ5QV/Scenario2.png)](https://postimg.cc/bSQRy5rZ)
Gambar di atas membutkikan pada ARP Cache sudah terdaftar IP Logika dan IP Physical sudah terdaftar sesuai dengan PC0 (192.168.1.1) jadi dari situ sudah tidak memerlukan broadcast.

### Ping PC1 ke PC0 (Reverse Ping) | Check ARP Cache | Scenario 3
[![Scenario3.png](https://i.postimg.cc/fyygmW1b/Scenario3.png)](https://postimg.cc/1VxHZSmx)
Gambar di atas seperti gambar pada scenario 2 jadi tidak perlu melakukan broadcast paket lagi karena sudah terdaftar pada ARP Cache.
Karena sewaktu menerima request (ping) dari PC 0 (192.168.1.1) sudah berisi MAC / Phsyical Address dari sumbernya.