128bits => Binary 2 Hexa => 4bits by 4bits

| 64 bits Network | 64 bits Hosts |

Ex: 
2001:0000:0000:0001:aabc:efa1:0000:000e

## Short ipv6 writting: ##
2001:::1:aabc:efa1::e

And again

2001::1:aabc:efa1::e


| Decimal | HexaDecimal | Binary |
|  ---    |     ---     |   ---  | 
|  0      |   0         |  0000  |
|  1      |   1         |  0010  |
|  2      |   2         |  0011  |
|  3      |   3         |  0100  |
|  4      |   4         |  0101  |
|  5      |   5         |  0110  |
|  6      |   6         |  0111  |
|  7      |   7         |  1000  |
|  8      |   8         |  1001  |
|  9      |   9         |  1010  |
|  10     |   A         |  1010  |
|  11     |   B         |  1011  |
|  12     |   C         |  1100  |
|  13     |   D         |  1101  |
|  14     |   E         |  1110  |
|  15     |   F         |  1111  |
	  

### Generate link local ipv6 addr ###
Take mac addr flip 7bit 0->1 or 1->0 and add in the middle FFFE

Ex: mac addr is on 48bits			

CA:01:E7:70:00:00

CA01.E770.0000

C    A    0    1    E    7    7    0    0    0    0    0
1100 1010 0000 0001 1110 0111 0111 0000 0000 0000 0000 0000

* Flip 7th bits

1100 1000 0000 0001 1110 0111 0111 0000 0000 0000 0000 0000

* Insert FFFE  => 1111 1111 1111 1110  in the middle

1100 1000 0000 0001 1110 0111       1111 1111 1111 1110         0111 0000 0000 0000 0000 0000
C    8    0    1    E    7          F    F    F    E            7    0    0    0    0    0 

C801:E7FF:FE70:0000

## Ex2 ##
ether 52:54:00:26:10:60 

5    2    5     4    0     0     2     6     1    0     6     0 
0101 0010 0101  0100 0000  0000  0010  0110  0001 0000  0110  0000

* Flip 7th bits
0101 0000 0101  0100 0000  0000  0010  0110  0001 0000  0110  0000

* Add FFFE in the middle
0101 0000 0101  0100 0000  0000  1111 1111 1111 1110   0010  0110  0001 0000  0110  0000

5    0    5     4    0     0     F    F    F    E      2     6     1    0     6     0   

5054:00FF:FE26:1060   

then just add  the network id here fe80:: => fe80:0:0:0


eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255
        inet6 fe80::5054:ff:fe26:1060  prefixlen 64  scopeid 0x20<link>
        ether 52:54:00:26:10:60  txqueuelen 1000  (Ethernet)
        RX packets 12082  bytes 1038845 (1014.4 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8738  bytes 898621 (877.5 KiB)
        TX errors 0  d ropped 0 overruns 0  carrier 0  collisions 0


### Multicast group because arp and broadcast does not work in ipv6 ###
multicast group
ff02::1
ff02::2


ff02::1 + The 20 last bits of the IP
ex:  inet6 fe80::5054:ff:fe26:1060  => (26:1060)  ff02::1:ff26:1060



