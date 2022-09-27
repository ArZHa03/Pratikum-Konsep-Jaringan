# Documentation Task Packet-Tracer [VLAN With DHCP]
## Topologi
[![Topologi.png](https://i.postimg.cc/Jn4Wj82G/Topologi.png)](https://postimg.cc/QBPPr2s3)
Topologi di atas terdiri dari 1 router, 1 switch, dan 8 pc-client dengan 3 VLAN (192.168.10.0/24 - 10 [admin] || 192.168.20.0/24 - 20 [dev] || 192.168.30.0/24 - 30 [manager]). Pada dasarnya VLAN, perangkat utamanya ialah Switch.

### Register VLAN Database At Router And Switch
[![VLANDatabase.png](https://i.postimg.cc/qM90S9z5/VLANDatabase.png)](https://postimg.cc/rKCvtZG1)
|  Devices 	| VLAN Number 	| VLAN Name 	|
|:--------:	|:-----------:	|:---------:	|
| Router 0 	|      10     	|   admin   	|
|          	|      20     	|    dev    	|
|          	|      30     	|  manager  	|
| Switch 0 	|      10     	|   admin   	|
|          	|      20     	|    dev    	|
|          	|      30     	|  manager  	|
| Switch 1 	|      10     	|   admin   	|
|          	|      20     	|    dev    	|
|          	|      30     	|  manager  	|
| Switch 2 	|      10     	|   admin   	|
|          	|      20     	|    dev    	|
|          	|      30     	|  manager  	|

### Add IP To Every VLAN With CLI At Router 0
[![Config-IPVLAN.png](https://i.postimg.cc/J7YRcymm/Config-IPVLAN.png)](https://postimg.cc/py8NPLp1)
Berikut perintah-perintah yang digunakan:
“Router#conf t”

“Router(config)#int gig0/0/0.10”
“Router(config-subif)#encapsulation dot1q 10”
“Router(config-subif)#ip add 192.168.10.1 255.255.255.0”

“Router(config)#int gig0/0/0.20”
“Router(config-subif)#encapsulation dot1q 20”
“Router(config-subif)#ip add 192.168.20.1 255.255.255.0”

“Router(config)#int gig0/0/0.30”
“Router(config-subif)#encapsulation dot1q 30”
“Router(config-subif)#ip add 192.168.30.1 255.255.255.0”

### Conifguration DHCP At Router With CLI
[![Config-DHCP.png](https://i.postimg.cc/g28dWNhk/Config-DHCP.png)](https://postimg.cc/pmW3QQkg)
Perintah-perintah yang digunakan:
“Router>en”
“Router#conf t”

“Router(config)#int gig0/0/0.10”
“Router(config-subif)#ip dhcp pool admin”
“Router(dhcp-config)#network 192.168.10.0 255.255.255.0”
“Router(dhcp-config)#default-router 192.168.10.1”
“Router(dhcp-config)#dns-server 192.168.10.1”
“Router(dhcp-config)#ip dhcp excluded-address 192.168.10.1”

“Router(config)#int gig0/0/0.20”
“Router(config-subif)#ip dhcp pool dev”
“Router(dhcp-config)#network 192.168.20.0 255.255.255.0”
“Router(dhcp-config)#default-router 192.168.20.1”
“Router(dhcp-config)#dns-server 192.168.20.1”
“Router(dhcp-config)#ip dhcp excluded-address 192.168.20.1”

“Router(config)#int gig0/0/0.30”
“Router(config-subif)#ip dhcp pool manager”
“Router(dhcp-config)#network 192.168.30.0 255.255.255.0”
“Router(dhcp-config)#default-router 192.168.30.1”
“Router(dhcp-config)#dns-server 192.168.30.1”
“Router(dhcp-config)#ip dhcp excluded-address 192.168.30.1”

### Configuration The VLAN In Every Port Connected At Every Switch
[![Config-Port-VLAN.png](https://i.postimg.cc/jjhbW2vp/Config-Port-VLAN.png)](https://postimg.cc/1g4T29kB)
|  Devices 	|    Interfaces    	|  Mode  	|     VLAN     	|
|:--------:	|:----------------:	|:------:	|:------------:	|
| Switch 0 	| Fa0/1 (Switch 1) 	|  Trunk 	|  Select All  	|
|          	|    Fa0/2 (PC0)   	| Access 	|  10 (admin)  	|
|          	|    Fa0/3 (PC1)   	| Access 	|   20 (dev)   	|
| Switch 1 	| Fa0/1 (Router 0) 	|  Trunk 	|  Select All  	|
|          	| Fa0/2 (Switch 0) 	|  Trunk 	|  Select All  	|
|          	| Fa0/3 (Switch 2) 	|  Trunk 	|  Select All  	|
|          	|    Fa0/4 (PC2)   	| Access 	|  10 (admin)  	|
|          	|    Fa0/5 (PC3)   	| Access 	|   20 (dev)   	|
|          	|    Fa0/6 (PC4)   	| Access 	| 30 (manager) 	|
| Switch 2 	| Fa0/1 (Switch 1) 	|  Trunk 	|  Select All  	|
|          	|    Fa0/2 (PC5)   	| Access 	|  10 (admin)  	|
|          	|    Fa0/3 (PC6)   	| Access 	|   20 (dev)   	|
|          	|    Fa0/4 (PC7)   	| Access 	| 30 (manager) 	|
Mode Trunk digunakan pada port yang terhubung dari Switch ke Switch atau ke Router.

### Set IP Configuration PC To DHCP
[![IPDHCPPC.png](https://i.postimg.cc/NfyBNgfX/IPDHCPPC.png)](https://postimg.cc/zV1svYhD)
| Devices 	| Interfaces 	|     IPv4     	| CIDR 	| Default Gateway 	|  DNS Server  	|
|:-------:	|:----------:	|:------------:	|:----:	|:---------------:	|:------------:	|
|   PC0   	|     Fa0    	| 192.168.10.6 	|  24  	|   192.168.10.1  	| 192.168.10.1 	|
|   PC1   	|     Fa0    	| 192.168.20.6 	|  24  	|   192.168.20.1  	| 192.168.20.1 	|
|   PC2   	|     Fa0    	| 192.168.10.5 	|  24  	|   192.168.10.1  	| 192.168.10.1 	|
|   PC3   	|     Fa0    	| 192.168.20.5 	|  24  	|   192.168.20.1  	| 192.168.20.1 	|
|   PC4   	|     Fa0    	| 192.168.30.3 	|  24  	|   192.168.30.1  	| 192.168.30.1 	|
|   PC5   	|     Fa0    	| 192.168.10.4 	|  24  	|   192.168.10.1  	| 192.168.10.1 	|
|   PC6   	|     Fa0    	| 192.168.20.4 	|  24  	|   192.168.20.1  	| 192.168.20.1 	|
|   PC7   	|     Fa0    	| 192.168.30.2 	|  24  	|   192.168.30.1  	| 192.168.30.1 	|

### Test Ping To Other VLAN
[![TestPing.png](https://i.postimg.cc/R0mmVK11/TestPing.png)](https://postimg.cc/hX262J5h)