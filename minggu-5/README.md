# Documentation Task Packet-Tracer (4) [VLAN]
## Topologi
[![Topologi.png](https://i.postimg.cc/nhM2bY78/Topologi.png)](https://postimg.cc/XrSd95Qx)
Topologi di atas terdiri dari 1 router, 1 switch, dan 3 pc-client dengan 2 VLAN (172.17.10.1/24 - 10 [IT] & 172.17.30.1/24 - 30 [DS]) dan 1 Non-VLAN (172.17.1.1/24). 

### Configuration IP (PC)
[![Config-IPPC.png](https://i.postimg.cc/BQncHcm8/Config-IPPC.png)](https://postimg.cc/w3nmdJ8H)

PC 0 :
IP Address -> 172.17.10.2
Subnet Mask -> 255.255.255.0
Gateway -> 172.17.10.1 (IP VLAN Router)
PC 1 :
IP Address -> 172.17.30.2
Subnet Mask -> 255.255.255.0
Gateway -> 172.17.30.1 (IP VLAN Router)
PC 2 :
IP Address -> 172.17.1.2
Subnet Mask -> 255.255.255.0
Gateway -> 172.17.1.1 (IP Router)

### Configuration IP (Router)
[![Config-IPRouter.png](https://i.postimg.cc/NMvkH3nY/Config-IPRouter.png)](https://postimg.cc/HJ3MGhHP)

Router 0 :
Interface Gig0/0/0 -> 172.17.1.1/24 (Configuration Non-VLAN IP)

### Conifguration VLAN Database (Switch)
[![Config-VLANDatabase-Switch.png](https://i.postimg.cc/XJKcc2M5/Config-VLANDatabase-Switch.png)](https://postimg.cc/YG9WtzC2)

Switch 0 :
VLAN NAME [IT] -> VLAN Number [10]
VLAN NAME [DS] -> VLAN Number [30]

### Conifugration Interface (Switch)
[![Config-Interfaces-VLANSwitch.png](https://i.postimg.cc/8ctRxjzP/Config-Interfaces-VLANSwitch.png)](https://postimg.cc/7JJJ2Pzp)

Switch 0 :
Interface FastEhernet0/1 -> Mode TRUNK & All VLAN (Configuration for Router)
Interface FastEhernet1/1 -> Mode Access & VLAN 10 [IT] (Configuration for PC0)
Interface FastEhernet2/1 -> Mode Access & VLAN 30 [DS] (Configuration for PC1)
Interface FastEhernet3/1 -> Mode Access & VLAN 1 [Default] (Configuration for PC2)

### Configuration VLAN Database (Router)
[![Config-VLANDatabase-Router.png](https://i.postimg.cc/BvKCtSMM/Config-VLANDatabase-Router.png)](https://postimg.cc/PLdDRjGw)

Router 0 :
VLAN NAME [IT] -> VLAN Number [10]
VLAN NAME [DS] -> VLAN Number [30]

### Conifguration IP VLAN (Router)
[![Config-IPVLANRouter.png](https://i.postimg.cc/BndTWW4D/Config-IPVLANRouter.png)](https://postimg.cc/VJWrMVSL)

Router 0 :
Interface Gig0/0/0.10 -> 172.17.10.1/24 (Configuration VLAN 10 [IT])
Interface Gig0/0/0.30 -> 172.17.30.1/24 (Configuration VLAN 30 [DS])

### Test Ping To Other VLAN And Non-VLAN
[![TestPing.png](https://i.postimg.cc/kXJwwdgg/TestPing.png)](https://postimg.cc/LhWz6wPc)

Ping di atas berasal dari PC0-172.17.10.2/24 (VLAN 10 [IT]) berhasil melakukan ping pada IP dari PC1-172.17.30.2/24 (VLAN 30 [DS]) yang dimana kedua IP tersebut berbeda network dan subnetting tanpa bantuan routing static karena pada Router 0 mereka terkoneksi secara Directly Connected dan bukan Remote Network.

[![Show-IPRoute-Router.png](https://i.postimg.cc/9FgPpRkL/Show-IPRoute-Router.png)](https://postimg.cc/XpFyNJ45)

Sehingga tidak diperlukan routing static atau semacamnya, VLAN seakaan terdapat 2 kabel pada router dengan IP yang berbeda. Dengan menambahkan IP pada virtual dengan imbuhan [.number] pada interfaces yang terkoneksi pada router secara nyata.