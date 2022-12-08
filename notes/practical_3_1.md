# Stimulating OSPF in a single area topology

## Configuring Router IP

###R0
```
en
conf t
int s1/0
ip add 192.168.1.1 255.255.255.0
no sh
```

### R1

```
en
conf t
int s1/0
ip add 192.168.1.2 255.255.255.0
no sh
int s1/1
ip add 192.168.2.2 255.255.255.0
no sh
```

### R2

```
en
conf t
int s1/0
ip add 192.168.2.3 255.255.255.0
no sh
```

## Configuring OSPF network

### R0
```
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
```
### R1
```
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
network 192.168.2.0 0.0.0.255 area 0
```

### R2

```
router ospf 1
network 192.168.2.0 0.0.0.255 area 0
```
