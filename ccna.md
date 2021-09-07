---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
title: CCNA
permalink: /ccna/
---
# CCNA Notes

- [CCNA Notes](#ccna-notes)
  - [Networking Basics](#networking-basics)
  - [TCP/IP Model](#tcpip-model)
    - [Important ports to remember & their protocol](#important-ports-to-remember--their-protocol)
    - [Port Ranges](#port-ranges)
  - [Binary](#binary)
  - [Hexadecimal](#hexadecimal)
  - [IP Addressing](#ip-addressing)
    - [Address Classes](#address-classes)
    - [Special Addresses](#special-addresses)
  - [Subnetting](#subnetting)
  - [Data Flows](#data-flows)
  - [Toplogies](#toplogies)
  - [Mac Address](#mac-address)
  - [CSMA/CD](#csmacd)
  - [Cables](#cables)
  - [Network Devices](#network-devices)
  - [Duplexes and Speeds](#duplexes-and-speeds)
  - [IP & Connections](#ip--connections)
  - [OSPF](#ospf)
  - [Multicast](#multicast)
  - [Networking Basics](#networking-basics-1)
  - [Helpful Commands](#helpful-commands)
  - [Resources](#resources)
  - [helpful links](#helpful-links)


## Networking Basics
- What is network?
  - Built to share resources

- Basic Networks
  - Bus Network
    - All devices attach along an ethernet cable
      - i.e. with vampire taps

- Networking Devices
  - Repeater
    - amplified/repeats signal from 1 port to another
    - layer 1
  - Hub
    - a "multi-port repeater"
      - repeated signal from 1 port to all ports
      - layer 1 
  - Switch
    - can read frames and uses MAC address table
    - works at layer 2 but can work at layer 3 if its a managed switch with routing capabilities
    - uses hardware ASICs
  - Bridge
    - intermediate device between switch and hub
    - learned MAC addresses via software
  - Router
    - allows routing between networks
    - layer 3
  - Access Points
    - Can be lightweight or autonomous
  - Wireless LAN Controller
    - Used to manage multiple Access Points


## TCP/IP Model
- Newest Version of CCNA is using hybrid tcp/ip model:
  - 5 Application
        - PDU = application data
  - 4 Transport
        - PDU = Segments
        - TCP
          - Connection oriented protocol
          - Transmitter -> SYN      ->   Receiver
          - Transmitter <- SYN ACK  <-   Receiver
          - Transmitter -> ACK      ->   Receiver
          - provides acknowledgment and reliability
          - MTU
            - maximum transmission unit
            -   MTU of FastEthernet is 1500 bytes 
            -   TCP supports 65495
        -   MSS (Maximum Segment size)
            -   largest amount of data to be sent
        -   TCP uses flow control to avoid sending data too quickly
            -   if sender is sending data faster than receiver can handle it drops data and requires re-transmission 
            - Header
              - 16 bit source port, 16 bit destination port
              - 32 bit sequence number
              - 32 bit acknowledgment number
              - header length, reserved, flags, window size
              - 16bit tcp checksum, 16 bit urgent pointer
              - options
              - data
        - UDP
          - delivery not guaranteed
          - Header
            - 16 bit source port, 16bit destination port
            - 16 bit UDP length, 16 bit UDP checksum
            - data
  - 3 Network
        - PDU = Packets
        - IP Protocol is not connection oriented like TCP
          - Packets are treated independently and may take different paths
          - IP is a best effort delivery system with no data recovery features
  - 2 Data Link
        - PDU = Frames
        - if Type field = 0x800 that indicates ipv4
        - if Type field = 0x806 that indicates arp
  - 1 Physical
        - PDU = Bits

### Important ports to remember & their protocol
|Service|Port|Protocol|
|---|---|---|
|FTP data   |20   	    |TCP     	|
|FTP command|21   	    |TCP     	|
|ssh  	    |22  	    |UDP     	|
|Telnet	    |23  	    |UDP     	|
|smtp	    |25  	    |TCP     	|
|DNS   	    |53  	    |TCP & UDP 	|
|TFTP  	    |69  	    |UDP     	|
|http   	|80   	    |TCP        |
|pop3   	|110   	    |TCP        |
|https 	    |443     	|TCP     	|

### Port Ranges
- System ports = 0 - 1023
- User ports = 1024 - 49151
- dynamic/private/ephemeral ports = 49152 -65535
- these ranges can change depending on OS 

## Binary
#Table

|Exponent|2^7|2^6|2^5|2^4|2^3|2^2|2^1|2^0|
|---|---|---|---|---|---|---|---|---|
|Binary|1|1|1|1|1|1|1|1|
|Decimal|128|64|32|16|8|4|2|1|

## Hexadecimal

|Hexadecimal   	|Binary   	|Decimal   	|
|---	|---	|---	|
|   0	|0000  	|   0	|
|   1	|0001  	|   1	|
|   2	|0010  	|   2	|
|   3	|0011  	|   3	|
|   4	|0100  	|   4	|
|   5	|0101  	|   5	|
|   6	|0110  	|   6	|
|   7	|0111  	|   7	|
|   8	|1000  	|   8	|
|   9	|1001  	|   9	|
|   A	|1010  	|   10	|
|   B	|1011  	|   11	|
|   C	|1100  	|   12	|
|   D	|1101  	|   13	|
|   E	|1110  	|   14	|
|   F	|1111  	|   15	|

## IP Addressing
- 32 bits total with 4 octets
  - x.x.x.x
- Routers maintain routing tables that use network addresses
### Address Classes
- Class A = 0.0.0.0 - 127.255.255.255 = unicast
  - 127.x.x.x is reserved for loopback
  - 0 is reserved for network
- Class B 128.0.0.0 - 191.255.255.255 = Unicast
- Class C 192.0.0.0 - 223.255.255.255 = Unicast
- Class D = 224.0.0.0 - 239.255.255.255  multicast
- Class E = 240.0.0.0 - 255.255.255.255 reserved for future or experimental purposes
- These classes have largely been replaced by CIDR
- IPv6 = no class addresses


### Special Addresses
- Directed broadcast address
  - host sends data to all devices on a specific network
    - i.e. network 172.31.0.0 would see a directed broadcast of 173.31.255.255
  - routers can be programmed to route directed broadcasts but it's usually disabled by default
- Local Broadcast Address
  - used to communicate with all devices on a local network
  - the request would look like 255.255.255.255
  - always dropped by routers unless DHCP helpers & relays are in place 
- Local Loopback address
  - 127.X.X.X ( usually 127.0.0.1)
  - or ::1 for ipv6
  - used to test a devices TCP/IP stack
- RFC1918 addresses
  - private and non-routable addresses
    - 10.0.0.0/8
    - 172.16.0.0/12
    - 192.168.0.0/16
- IPv4 Link-Local Addresses
  - RFC 3927 Automatic Private IP Address ( APIPA)
  - non-routable
- Subnet Masks
  - if 2 devices are on the same subnet they may not need a default gateway. If they are not on the same subnet they may require a default gateway to communicate
- CIDR
  - Classless inter-domain routing
  - Variable length subnet mask (VLSM)
  - 

## Subnetting

-Subnetting when given an IP
172.17.34.122 / 20
172.17.X.122
X = the binary equivalent of 34

128 64  32  16 | 8   4   2   1
0   0   1   0  | 0   0   1   0

172.17.32.0     | set host bits to all 0s to get network
172.17.32.1     | add 1 host bit to get first host address
172.17.47.254   | subtract 1 host bit from broadcast address
172.17.47.255   | set all host bits to 1s

- Subnetting for hosts
  - 2 ^ N -2
- Subnetting for Networks
  - 2 ^ N 

  - 10.123.192.0/18

needs 31 subnets with as many hosts as possible
Formula is 2 ^ N so that means to get to >= 31 you need 5 bits ( which comes out to be 32)

10.123.X.0
X

128 64 | 32  16  8   4   2  | 1
1   1  | 0   0   0   0   0   | 0
        These  5 boys are stolen
10.123.192.0/23

next subnet would be 
128 64 | 32  16  8   4   2  | 1
1   1  | 0   0   0   0   1   | 0
10.123.194.0/23

then 
128 64 | 32  16  8   4   2  | 1
1   1  | 0   0   0   1   0   | 0
10.123.196.0/23

then
128 64 | 32  16  8   4   2  | 1
1   1  | 0   0   0   1   1   | 0
10.123.198.0/23

these binary combinations continue so on and so on`
- Helpful Table

|2|^|result|
|---|---|---|
|2|1|2|
|2|2|4|
|2|3|8|
|2|4|16|
|2|5|32|
|2|6|64|
|2|7|128|
|2|8|256|
|2|9|512|
|2|10|1024|


## Data Flows
- unicast
  - a one to one
- broadcast
  - one to all
  - not supported in ipv6
- multicast
  - one to subscribed clients 
  
## Toplogies
- Bus
  - all clients share 1 line
  - examples are thicknet and thinnet
    - thinnet is an ethernet variant
      - max speed of 10 mbps & used coax

## Mac Address
- Media access control
- 48 bits

## CSMA/CD
- Carrier sense Multiple Access/Collision detection
- used with ethernet
  - Carrier sense tries to sense what is speaking on network
  - multiple access is any device can try to communicate as long as no other devices are talking
  - when ethernet determines a collision  has taken place it sends a jamming signal and then send a random backoff delay signal
  - the longer the cable & the more hosts the more chances of collisions 

## Cables
- 10Base2
  - Coax cable 
  - 10mbps
  - 185 meters max
  - baseband
- 10baseT
  - ethernet & rj45 cables
  - 10mbps
  - usually unshielded twisted pair cables unless a noisy environments calls for a shielded twisted pair
  - 100 meters
  - T means twisted pair
- UTP types
  - T568A
  - T568B
    - more popular but both should work as they wire a cable straight through
- Straight through cables
  - connects from endpoint to switch/hub
  - MDI ( media independent interface) = ethernet port connection
- Crossover cable
  - used when connection like devices
- Cat1
  - previously used for telephones
- Cat2 
  - used for telephones and data with speeds up to 4mbps
- Cat3
  - used for networks up to 10 mbps but now used for telephones
  - typically used in distances up to 100m
- Cat4
  - 20mhz & 16mbps
- Cat5
  - 100 mhz & 10/100
- Cat5E
  - 100mhz and 1gbps
  - 100 meter distance
- Cat6 
  - 250mhz and 10gbps up to 55m
  - 100meter distance at 1gbps
- Cat6A
  -  500MHZ 10gbps up to 100meters
- Cat7
  - 600MHZ
  - 10gbps up to 100meters
  - can use tera connector
- Cat7a
  - 1000mhz
  - 100mbps and up to 40gbps and 100gbps up to 50meters
  - for new installs go with cat 6a or cat7
- Cat8
  - 40gbps
- DAC
  - Direct attachment cable
  - copper twinax with SFPs on each side
  - supports up to 10gbps
  - works up to 15m
    - SFP is hot pluggable
- Rollover cable
  - special cable that connects to console ports of routers
  - usually its a console to db9 

## Network Devices
- Hub
  - layer 1 device
  - 10baseT
  - multiport repeater
  - 1 big dumb collision domain
- Bridge
  - layer 2/data link
  - has MAC address & cam table
  - uses software to do processing
  - each interface is a separate collision domain
  - does not separate broadcast domains
- Switches
  - uses hardware for processing & uses ASICs
  - layer 2 usually
  - has mac address table
  - will flood broadcast and multicast traffic by default
- Routers
  - layer 3 devices
  - network layer
  - routes via IP addresses


## Duplexes and Speeds
- happens when autonegotation fails or manual configurations are incorrect
- causes performance issues 

## IP & Connections
- 


## OSPF
- Open Shortest Path First
- Link State routing protocol


## Multicast 
- Devices that need to receive multicast video will join a group
- Uses Class D address 224.0.0.0 - 239.255.255.255
  - 224.0.0.0 - 224.0.0.255 = reserved for link local address
  - OSPF reserved for 224.0.0.5 - 224.0.0.6
  - rip v2 reserves 224.0.0.9 
  - eigrp reserves 224.0.0.10
  - 224.0.1.0 - 238.255.255.255 reserved for globally scoped addresses
  - Source Specific Multicast addresses reserves 232.0.0.0 - 232.255.255.255 
  - 233.0.0.0 - 233.255.255.255 reserved for  GLOP addresses
    - based on Autonomous system numbers
  - 239.0.0.0 - 239.255.255.255 limited scope address
    - kind of like 172.16.x.x and 192.168.1.x
- ### IGMP
  - IGMPv2 allows receivers to leave IGMP Groups, IGMPv1 didn't do that
  - Switches must be programmed for IGMP snooping. 
  - IGMPv3 allows a receiver to choose a source device
  - Multicast can do Reverse Path forwarding check to prevent receiving duplicate copies of data
  - PIM
    - protocol independent multicast
      - a type of multicast routing protocol
      - PIM dense mode
      - initial multicast traffic gets flooded and then pruned and could be every 3 min.
      - PIM sparse mode
        - a shared distribution tree
        - you set a router as a rendezvous point
        - no flooding
        - 

## Networking Basics
- Vlans
  - vlan = a broadcast domain = logical network (subnet)
  - when a frame arrives @ switch it gets tagged
  - trunking
    - ISL
      - cisco proprietary
    - 802.1q
  - Trunk ports allow you to send VLAN info across ports for multiple vlans
  - 802.1q frame 
    - has a "Tag" inserted into it that contains 4 parts & the 2 main parts are TPID (0x8100) (Tag Protocol IDentifier) and VLAN ID
  - Native VLANs
    - untagged
    - when a port on a switch is set up as a trunk it can send and receive tagged frames. frames belonging to native vlan do not carry vlan tags. if an untagged frame hits the trunk it will travel across native vlan
    - management traffic like STP BPDU and DTP will use native vlan
    - some management traffic always uses vlan 1 if vlan 1 is left as native vlan untagged. if native vlan was changed it will tag the traffic with that vlan 
      - CDP
      - VTP
      - PAgP
      - UDLD
    - Native vlan could be used so that you can tag voip traffic from phones, then have the PC it's connected to use the native vlan. May boost security by preventing PC from being able to communicate or eavesdrop on phone
      - you can use 1 subnet for the voip vlan and 1 subnet for the pc/data vlan
    - Vlans can be assigned
      - statically by admin
      - dynamic vlan
        - VMPS (vlan membership policy server)
          - based on source mac address & cisco proprietary
        - Voice vlan
          - used by ip phones
    - VTP
      - cisco prop layer 2 protocol
      - allows propagation of vlan info across trunk links
      - vlan config can get wiped out if done incorrectly
      - 

## Helpful Commands
- `hostname Router1`
- `ip address 192.168.1.1 255.255.255.0 `
- `enable password cisco`
- `conf t -> service password-encryption` makes enable password encrypted
- `enable secret cisco123` secret password overrides enable password
- `conf t -> line vty 0 4 -> transport input telnet -> password cisco -> login`
- `conf t -> line con 0 -> password cisco`
- `conf t -> line con 0 -> login`


## Resources

## helpful links
 [Cisco's intro to packet tracer](https://www.netacad.com/courses/packet-tracer/introduction-packet-tracer)
[exam topic list](https://www.cisco.com/content/dam/en_us/training-events/le31/le46/cln/marketing/exam-topics/200-301-CCNA.pdf)
1.0 Network Fundamentals = 20%
Network Access = 20%
IP connectivity = 25%
IP services = 10%
Security fundamentals = 15%
Automation and programmability = 10%

[free webinars from Ivan Pepelnjak](https://www.ipspace.net/Subscription/Free)

[David Bombals binary/decimal/subnetting] quizzes(https://davidbombal.com/free-quiz/)

[Network Chuck's sweet Fiber video](https://youtu.be/E3DEJ7odWq0)