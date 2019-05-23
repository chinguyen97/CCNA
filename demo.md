## Lap

### Router

Would you like to enter the initial configuration dialog ? 

write erase

reload

Router 

- hostname: 
R1(config)#hoestname R1
- Pass
	+R1(config)#enable password (123)
	+R1(config)#enable secret(123)
show version (IOS)
- ssh
R1(config)#username chi password 123
R1(config)# ip domain-name mdt.lab
R1(config)#crypto key generate rsa
R1(config)#line vty 0 15
R1(config-line)#transport input ssh
R1(config-line)#login

- Nat

### SW l3
- Caaus hinfh vlan 
+ Bat tinh nang dinh tuyen: ip routing
+ Tao vln va gan int tuong ung
L3(config)#vlan 81
L3(config)#int vlan 81
L3(config-f)# ip add 192.168.81.1 255.255.255.0

L3(config)#vlan 82
L3(config)#int vlan 82
L3(config-f)# ip add 192.168.82.1 255.255.255.0

- trunk

L3(config)#int f0/2
L3(config-f)#switch port trunk encapsu dot1q
L3(config-f)#sw p mode trunk
-vtp
L3(config)#vtp mode server
L3(config)#vtp domain mdt
L3(config)#vtp password 123

-dhcp

R1(config)#ip dhcp pool vlan81
R1(dhcp-config)#network 192.168.81.0 255.255.255.0
R1(dhcp-config)#default-router 192.168.81.1
R1(dhcp-config)#dns-server 8.8.8.8
R1(config)#ip dhcp pool vlan82
R1(dhcp-config)#network 192.168.82.0 255.255.255.0
R1(dhcp-config)#default-router 192.168.82.1
R1(dhcp-config)#dns-server 8.8.8.8

- inter vlan 

### SW l2

- trunk
L3(config)#int f0/1
L3(config-f)#switch port mode trunk
L3(config-f)#switch port trunk allowed valn 81,82
-vtp client
L2(config)#vtp mode client
L2(config)#vtp domain mdt
L2(config)#vtp password 123


#### Mt