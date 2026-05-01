#### ========R0=========

en

conf t



interface gig0/0/0

ip address 192.168.1.1 255.255.255.192

ip helper-address 192.168.1.129

no shutdown



interface se 0/1/0

ip address 192.168.1.137 255.255.255.252

no shutdown



ip route 0.0.0.0 0.0.0.0 192.168.1.138



#### ========R1=========

en

conf t



interface gig0/0/0

ip address 192.168.1.65 255.255.255.224

ip helper-address 192.168.1.129

no shutdown



interface se 0/1/0

ip address 192.168.1.138 255.255.255.252

no shutdown



interface se 0/1/1

ip address 192.168.1.141 255.255.255.252

no shutdown



ip route 192.168.1.0 255.255.255.192 192.168.1.137

ip route 192.168.1.96 255.255.255.240 192.168.1.142

ip route 192.168.1.112 255.255.255.240 192.168.1.142

ip route 192.168.1.128 255.255.255.248 192.168.1.142



#### ========R3=========

en

conf t



interface gig0/0/0

ip address 192.168.1.129 255.255.255.248

no shutdown



interface se 0/1/0

ip address 192.168.1.142 255.255.255.252

no shutdown



interface se 0/1/1

ip address 192.168.1.145 255.255.255.252

no shutdown





ip dhcp excluded-address 192.168.1.1

ip dhcp excluded-address 192.168.1.65

ip dhcp excluded-address 192.168.1.97

ip dhcp excluded-address 192.168.1.113

ip dhcp excluded-address 192.168.1.129 192.168.1.131



ip dhcp pool UTILITIES

network 192.168.1.0 255.255.255.192

default-router 192.168.1.1

dns-server 192.168.1.130



ip dhcp pool CITY\_HALL

network 192.168.1.64 255.255.255.224

default-router 192.168.1.65

dns-server 192.168.1.130



ip dhcp pool VLAN10

network 192.168.1.96 255.255.255.240

default-router 192.168.1.97

dns-server 192.168.1.130



ip dhcp pool VLAN20

network 192.168.1.112 255.255.255.240

default-router 192.168.1.113

dns-server 192.168.1.130





ip route 192.168.1.0 255.255.255.192 192.168.1.141

ip route 192.168.1.64 255.255.255.224 192.168.1.141

ip route 192.168.1.96 255.255.255.240 192.168.1.146

ip route 192.168.1.112 255.255.255.240 192.168.1.146



#### ========R2=========

en

conf t



interface g0/0/0

no shutdown



interface g0/0/0.10

encapsulation dot1Q 10

ip address 192.168.1.97 255.255.255.240

ip helper-address 192.168.1.129



interface g0/0/0.20

encapsulation dot1Q 20

ip address 192.168.1.113 255.255.255.240

ip helper-address 192.168.1.129



interface se 0/1/0

ip address 192.168.1.146 255.255.255.252

no shutdown



ip route 0.0.0.0 0.0.0.0 192.168.1.145

