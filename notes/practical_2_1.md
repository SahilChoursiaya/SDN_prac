# Stimulating VLAN With Single Switch
## Config for switch 0
en
conf t
vlan 10
name upper
vlan 20
name lower

int f0/1
switchport mode access
switchport access vlan 10

int f0/2
switchport mode access
switchport access vlan 10

int f0/3
switchport mode access
switchport access vlan 20

int f0/4
switchport mode access
switchport access vlan 20

