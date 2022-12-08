# Stimulating OSPF in a Multi area topology

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
int s1/1
ip add 192.168.3.3 255.255.255.0
no sh
```

### R3

```
en
conf t
int s1/0
ip add 192.168.3.4 255.255.255.0
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
network 192.168.3.0 0.0.0.255 area 1 
```

### R3

```
router ospf 1
network 192.168.3.0 0.0.0.255 area 1
```

## Ping Other devices

### R1
```
do ping 192.168.2.3
```
should be successful.

```
do ping 192.168.3.4
```
should be unsuccessful.

