# Documentation Task Packet-Tracer (3) [Routing]
## Topologi
[![Topologi-One-Router-Two-Network.png](https://i.postimg.cc/vB1WvSyW/Topologi-One-Router-Two-Network.png)](https://postimg.cc/k6m6JsB4)
Topologi di atas terdiri dari 1 router, 2 switch, dan 4 pc-client. Jumlah Netowrk di atas ada 2 dengan configurasi kelas C yakni 192.168.10.0/24 & 192.168.20.0/24.

### Configuration IP (PC)
[![IPConfig-PC.png](https://i.postimg.cc/FKHbYHnC/IPConfig-PC.png)](https://postimg.cc/18bVTsSD)
PC 0 :
IP Address -> 192.168.10.2
Subnet Mask -> 255.255.255.0
Gateway -> 192.168.10.1 (IP Router)
PC 1 :
IP Address -> 192.168.10.3
Subnet Mask -> 255.255.255.0
Gateway -> 192.168.10.1 (IP Router)
PC 2 :
IP Address -> 192.168.20.2
Subnet Mask -> 255.255.255.0
Gateway -> 192.168.20.1 (IP Router)
PC 3 :
IP Address -> 192.168.20.3
Subnet Mask -> 255.255.255.0
Gateway -> 192.168.20.1 (IP Router)
### Configuration IP (Router) 
[![IPConfig-Router.png](https://i.postimg.cc/pdcfzMwW/IPConfig-Router.png)](https://postimg.cc/4KtHRq4q)
Router 0 :
Interface Gig0/0/0 -> 192.168.10.1/24 (Configuration for network id 192.168.10.0/24)
Interface Gig0/0/1 -> 192.168.20.1/24 (Configuration for network id 192.168.20.0/24)

### Test Ping From Network 192.168.10.0/24 To 192.168.20.0/24 Or Reverse
[![Ping-PC1-To-PC3.png](https://i.postimg.cc/Z5cFYdjy/Ping-PC1-To-PC3.png)](https://postimg.cc/CRRfmd3F)
Terlihat ketika ping pertama dan kedua RTO (request time out) karena untuk pertama kali pada layer data-link mac belum ada sehingga ping tersebut ditunda dan digantikan dengan package broadcast untuk dari PCn1 (192.168.10.3/24) ke Router 0 (192.168.10.1/24) -> untuk RTO pertama. Sementara RTO kedua digantikan dengan packgage broadcast dari Router 0 (192.168.10.1/24) ke PC 3 (192.168.20.3/24) untuk mendapatkan MAC / Phsyical Address. Terlihat pada arp -a (arpa cache) pada PC0 (192.168.10.2/24) memiliki daftar arp yaitu 192.168.10.1 (IP Router 0) dengan Physical / MAC Address 0001.427c.9c01.
[![Ping-PC3-To-PC1.png](https://i.postimg.cc/g2dHPDyW/Ping-PC3-To-PC1.png)](https://postimg.cc/xcxzvLFx)
Terlihat gambar di atas PC3-192.168.20.3/24 tidak melakukan request ping dan hanya replay ping sebelumnya dari PC0-192.168.10.2/24 dan sudah memiliki daftar arpa cache yaitu IP 192.168.20.1 (Router 0) dengan Physical / MAC Address 0001.427c.9c02 sehingga untuk memalukan ping pada PC3-192.168.20.3/24 ke PC1-192.168.10.3/24 tidak terjadi RTO lagi.
### Test Ting Ping From Self Netowrk
[![Ping-PC2-To-PC3.png](https://i.postimg.cc/ZndxJsDT/Ping-PC2-To-PC3.png)](https://postimg.cc/H8Ty2zgK)
Terlihat pada gambar di atas PC2-192.168.20.2/24 melakukan request ping ke PC3-192.168.20.3/24 tidak terjadi RTO meski baru pertama kali di jalankan. Karena pada Router 0 (192.168.20.1/24) sudah memiliki tabel routing ke PC1-192.168.10.3/24 dan PC3-192.168.20.3/24 dari test ping sebelumnya.
Dan pada test sebelumnya (Request Ping From Network A To Network B) tidak diperlukan routing karena hanya ada satu router. Karena fitur dari "Directly Connected Network".
#### Directly Connect Network & Remote Network
Untuk dapat membaca dan memahami tabel routing dengan baik, harus dipahami terlebih dahulu tentang directly network (network yang terhubung langsung) dan remote network (network yang tidak terhubung langsung) dari sebuah router. Untuk menjangkau remote network, sebuah router memerlukan router lain sebagai next hop atau gateway. Perhatikan topologi berikut ini:
[![Tabel-2-BRouting-2-300x143.png](https://i.postimg.cc/SsfdK63B/Tabel-2-BRouting-2-300x143.png)](https://postimg.cc/jwCPg7sc)
Pada jaringan di atas, dapat diketahui directly connected network dan remote network pada masing router sebagai berikut:

    Directly Connected Network:
        Pada router R1:
            Terhubung ke ether1: Network Id 192.168.10.0/24
            Terhubung ke ether2: Network Id 192.168.40.0/30
        Pada router R2:
            Terhubung ke ether1: Network Id 192.168.40.0/30
            Terhubung ke ether2: Network Id 192.168.20.0/24
            Terhubung ke ether3: Network Id 192.168.30.0/24
    Remote Network:
        Pada router R1:
            Network Id 192.168.20.0/24
            Network Id 192.168.30.0/24
        Pada router R2:
            Network Id 192.168.10.0/24
[![Screenshot-20220918-142841.png](https://i.postimg.cc/bNcn5D5b/Screenshot-20220918-142841.png)](https://postimg.cc/8s4sJ5NP)