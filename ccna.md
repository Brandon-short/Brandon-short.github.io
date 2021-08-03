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
  - [OSPF](#ospf)
  - [Multicast](#multicast)
  - [Networking Basics](#networking-basics-1)
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
  - 5. Application
        - PDU = application data
  - 4. Transport
        - PDU = Segments
        - TCP
          - Connection oriented protocol
          - Transmitter -> SYN      ->   Receiver
          - Transmitter <- SYN ACK  <-   Receiver
          - Transmitter -> ACK      ->   Receiver
        - UDP
          - 
  - 3. Network
        - PDU = Packets
        - IP Protocol is not connection oriented like TCP
          - Packets are treated independently and may take different paths
          - IP is a best effort delivery system with no data recovery features
  - 2. Data Link
        - PDU = Frames
        - if Type field = 0x800 that indicates ipv4
        - if Type field = 0x806 that indicates arp
  - 1. Physical
        - PDU = Bits

### Important ports to remember & their protocol
|Service   	|Port      	|Protocol   |
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