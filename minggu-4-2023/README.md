# Documentation Task Packet-Tracer (2) [Routing]
## Topologi
[![Topologi-2.png](https://i.postimg.cc/1zYjm96p/Topologi-2.png)](https://postimg.cc/67n0zxM3)
Topologi di atas terdiri dari 2 pc client dan 2 router dengan subneting.

### Configuration IP (PC)
[![IPConfig-PC.png](https://i.postimg.cc/wMDfQLrV/IPConfig-PC.png)](https://postimg.cc/RJVLM646)
PC 0 :
IP Address -> 192.168.1.2
Subnet Mask -> 255.255.255.0
Gateway -> 192.168.1.1 (IP Router)
PC1 :
IP Address -> 192.168.3.2
Subnet Mask -> 255.255.255.0
Gateway -> 192.168.3.1 (IP Router)

### Configuration IP (Router) 
[![IPConfig-Router.png](https://i.postimg.cc/j5wkCGQB/IPConfig-Router.png)](https://postimg.cc/PpHMRV7M)
Router 0 :
Interface Gig0/0/0 -> 192.168.1.1/24 (Configuration for pc client)
Interface Gig0/0/1 -> 192.168.2.1/24 (Configuration for routing)
Router 1 :
Interface Gig0/0/0 -> 192.168.3.1/24 (Configuration for pc client)
Interface Gig0/0/1 -> 192.168.2.2/24 (Configuration for routing)

### Configuration Static Route (Router)
[![Config-Route-Static.png](https://i.postimg.cc/hjkZmp2v/Config-Route-Static.png)](https://postimg.cc/ftvvnjnQ)
Untuk setting static routing di cisco packet tracer menggunakan perintah :
#ip route [destination] [subnet] [next hop address]
Keterangan :
- ip route : perintah membuat tabel routing static
- destination : network jaringan yang dituju
- subnet : subnet mask jaringan yang dituju
- next hop address : ip dari router yang akan dilewati

IP Route (Router 0) :
192.168.3.0/24 via 192.168.2.2
[for sending packages or ping from PC0-192.168.1.2/24 to PC1-192.168.3.2/24]
IP Route (Router 1) :
192.168.1.0/24 via 192.168.2.1
[for sending packages or ping from PC1-192.168.3.2/24 to PC0-192.168.1.2/24]

### Test Ping From Network 192.168.1.0/24 To 192.168.3.0/24 Or Reverse
[![Ping-PC0-To-PC1.png](https://i.postimg.cc/d00fc77s/Ping-PC0-To-PC1.png)](https://postimg.cc/cvVhQLM2)
Terlihat ketika ping pertama dan kedua RTO (request time out) karena untuk pertama kali pada layer data-link mac belum ada sehingga ping tersebut ditunda dan digantikan dengan package broadcast untuk dari PC 0 (192.168.1.2/24) ke Router 0 (192.168.1.1/24) -> untuk RTO pertama. Sementara RTO kedua digantikan dengan packgage broadcast dari Router 0 (192.168.2.1/24) ke Router 1 (192.168.2.2/24) untuk mendapatkan MAC / Phsyical Address. Terlihat pada arp -a (arpa cache) pada PC0 (192.168.1.2/24) memiliki daftar arp yaitu 192.168.1.1 (IP Router 0) dengan Physical / MAC Address 0090.2148.aa01.
[![Ping-PC1-To-PC0.png](https://i.postimg.cc/x1CH9Nm8/Ping-PC1-To-PC0.png)](https://postimg.cc/ZCG0cRVz)
Terlihat gambar di atas PC1-192.168.3.2/24 tidak memalukan request ping dan hanya replay ping sebelumnya dari PC0-192.168.1.2/24 dan sudah memiliki daftar arpa cache yaitu IP 192.168.3.1 (Router 1) dengan Physical / MAC Address 0001.9724.4801 sehingga untuk memalukan ping pada PC1-192.168.3.2/24 ke PC1-192.168.1.2/24 tidak terjadi RTO lagi.