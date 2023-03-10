# ADMIN JARINGAN KELOMPOK - 2
 - 3121600025 - Ahmad Shonhaji
 - 3121600010 - Arga Rafi I.M
 - 3121600023 - Arianto Zaki Hamdalah
## LIST PROGRES MINGGU - 3


### 1. Reset Configuration Router - 2
Reset Konfigurasi dilakukan dengan menggunakan Winbox melalui Wine
Akses fitur di bagian sidebar pada menu System -> pilih Reset Configuration -> centang No Default Configuration -> klik Reset Configuration.
Setelah itu akan otomatis melakukan rebooting pada router dan aplikasi akan melakukan reconnecting.


### 2. Config IP Local & Public
Setelah rebooting akses fitur di sidebar pada menu IP -> Addresses -> klik tombol "+" ->
 #### ETHER 1
 - Address = 10.252.108.12/24
 - Network = 10.252.108.0
 - Interface = ETHER 1

 #### ETHER 2
 - Address = 192.168.2.1/24
 - Network = 192.168.2.1/24
 - Interface = ETHER 2

![](https://raw.githubusercontent.com/argarafiar/workshop_jaringan/main/minggu-3/address-list.png)

### 3. Config Default Route
Akses fitur di sidebar pada menu New Terminal
#### Configurasi Default Route
```console
ip route add dst-address=0.0.0.0/0 gateway=10.252.108.1
ip ro pr
```

### 3. Configurasi DNS
Akses fitur di sidebar pada menu IP -> DNS -> masukkan IP Server=202.9.85.3
![](https://raw.githubusercontent.com/argarafiar/workshop_jaringan/main/minggu-3/dns-setting.png)

### 4. Config Internet Client
 - Berikut konfigurasi lengkapnya
```console
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/ip pool
add name=dhcp_pool0 ranges=192.168.2.2-192.168.2.254
/ip dhcp-server
add address-pool=dhcp_pool0 disabled=no interface=ether2 name=dhcp1
/ip dhcp-server network
add address=192.168.5.0/24 gateway=192.168.5.1
/ip firewall nat
add action=masquerade chain=srcnat out-interface=ether1
```

### 5. Menambah IP Routes
Ketikkan pada New Terminal Winbox
```console
ip ro add gateway 10.252.108.11 dst 192.168.1.0/24
ip ro add gateway 10.252.108.13 dst 192.168.3.0/24
ip ro add gateway 10.252.108.14 dst 192.168.4.0/24
ip ro add gateway 10.252.108.15 dst 192.168.5.0/24
ip ro add gateway 10.252.108.16 dst 192.168.6.0/24
ip ro add gateway 10.252.108.17 dst 192.168.7.0/24
ip ro add gateway 10.252.108.18 dst 192.168.8.0/24
ip ro add gateway 10.252.108.19 dst 192.168.9.0/24
```
![](https://raw.githubusercontent.com/argarafiar/workshop_jaringan/main/minggu-3/Route%20list.png)

### 6. Tes ping antar client
![](https://raw.githubusercontent.com/argarafiar/workshop_jaringan/main/minggu-3/komjar2.png)
### 7. Export Config
Akses fitur di sidebar pada menu New Terminal, lalu ketikkan :
```console
export
```
dan file sudah berhasil di download ke komputer
