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
  - [Networking Basics](#networking-basics-1)
    - [Vlans](#vlans)
    - [STP](#stp)
    - [NAT](#nat)
  - [IP Routing](#ip-routing)
    - [Routing vs Routed protocols](#routing-vs-routed-protocols)
    - [Static vs Dynamic Routing](#static-vs-dynamic-routing)
    - [Determing best routes](#determing-best-routes)
    - [routing terms](#routing-terms)
    - [Types of routing protocols](#types-of-routing-protocols)
    - [Routing Protocols](#routing-protocols)
      - [OSPF](#ospf)
      - [Multicast](#multicast)
      - [IGMP](#igmp)
    - [Switch Stacking](#switch-stacking)
    - [QOS](#qos)
      - [Policers & Shapers](#policers--shapers)
      - [Queueing](#queueing)
    - [VOIP](#voip)
    - [GRE tunnels](#gre-tunnels)
  - [Wifi](#wifi)
  - [Helpful Commands](#helpful-commands)
    - [General Commands](#general-commands)
    - [VLANs](#vlans-1)
    - [STP/CDP/LLDP/Etherchannel](#stpcdplldpetherchannel)
    - [IP](#ip)
    - [HSRP (hot standby router protocol)](#hsrp-hot-standby-router-protocol)
    - [NTP](#ntp)
    - [SYSLOG](#syslog)
    - [SPAN ports](#span-ports)
    - [NAT](#nat-1)
    - [Routing](#routing)
      - [RIPv2](#ripv2)
      - [EIGRP](#eigrp)
      - [OSPF](#ospf-1)
  - [Resources](#resources)
  - [helpful links](#helpful-links)
  - [Shortcuts](#shortcuts)

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
  - `5 Application`
        - PDU = application data
  - `4 Transport`
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
  - `3 Network`
        - PDU = Packets
        - IP Protocol is not connection oriented like TCP
          - Packets are treated independently and may take different paths
          - IP is a best effort delivery system with no data recovery features
  - `2 Data Link`
        - PDU = Frames
        - if Type field = 0x800 that indicates ipv4
        - if Type field = 0x806 that indicates arp
  - `1 Physical`
        - PDU = Bits

### Important ports to remember & their protocol

|Service|Port|Protocol|
|---|---|---|
|FTP data   |20        |TCP      |
|FTP command|21        |TCP      |
|SSH       |22       |UDP      |
|Telnet     |23       |UDP      |
|SMTP     |25       |TCP      |
|DNS        |53       |TCP & UDP  |
|TFTP       |69       |UDP      |
|HTTP    |80        |TCP        |
|POP3    |110        |TCP        |
|HTTPS      |443      |TCP      |

### Port Ranges

- System ports = 0 - 1023
- User ports = 1024 - 49151
- dynamic/private/ephemeral ports = 49152 -65535
- these ranges can change depending on OS

## Binary

|Exponent|2^7|2^6|2^5|2^4|2^3|2^2|2^1|2^0|
|---|---|---|---|---|---|---|---|---|
|Binary|1|1|1|1|1|1|1|1|
|Decimal|128|64|32|16|8|4|2|1|

## Hexadecimal

|Hexadecimal    |Binary    |Decimal    |
|--- |--- |--- |
|   0 |0000   |   0 |
|   1 |0001   |   1 |
|   2 |0010   |   2 |
|   3 |0011   |   3 |
|   4 |0100   |   4 |
|   5 |0101   |   5 |
|   6 |0110   |   6 |
|   7 |0111   |   7 |
|   8 |1000   |   8 |
|   9 |1001   |   9 |
|   A |1010   |   10 |
|   B |1011   |   11 |
|   C |1100   |   12 |
|   D |1101   |   13 |
|   E |1110   |   14 |
|   F |1111   |   15 |

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
    - 10.0.0.0 - 10.255.255.255 - 10.0.0.0/8
    - 172.16.0.0 - 172.31.255.255 - 172.16.0.0/12
    - 192.168.0.0 - 192.168.255.255 192.168.0.0/16
- IPv4 Link-Local Addresses
  - RFC 3927 Automatic Private IP Address ( APIPA)
  - non-routable
  - 169.254.X.X/16
- Subnet Masks
  - if 2 devices are on the same subnet they may not need a default gateway. If they are not on the same subnet they may require a default gateway to communicate
- CIDR
  - Classless inter-domain routing
  - Variable length subnet mask (VLSM)

## Subnetting

- Subnetting when given an IP
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
  - one to many subscribed clients
  
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
  - 500MHZ 10gbps up to 100meters
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
- SFP vs SFP+
  - identical in appearance
  - SFP+ is newer and supports speeds up to 10 - 16gbps
  - SFP doesn't support 10gbps and is usually in 100mbits to 1gbps
- QSFP
  - Quad Small form-Factor Pluggables 
  - QSFP data rates get up to 1 Gbps per channel, allowing for 4X1 G cables and stackable networking designs that achieve better throughput
- QSFP+
  - QSFP+ can reach speeds of 10 Gbps per line. This makes it a 40G connection type
- QSFP28
  - QSFP28 (quad small form-factor pluggable 28) is designed for 100G applications


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
  - each port on switch is a seperate collision domain
  - does not break up your broadcast domains
- Routers
  - layer 3 devices
  - network layer
  - routes via IP addresses
  - all ports on router will be different broadcast domains

## Duplexes and Speeds

- happens when autonegotation fails or manual configurations are incorrect
- causes performance issues


## Networking Basics

### Vlans

- vlan = a broadcast domain = logical network (subnet)
- when a frame arrives @ switch it gets tagged
- trunking
  - ISL (Inter-Switch Link)
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
    - uses revision numbers
      - everytime a change is made to vlan database it increments by 1 then gets advertised to all VTP databases in domain
  - DTP
    - Dynamic trunking protocol
    - cisco proprietary
    - allows dynamic formation of trunks
    - 2 modes
      - dynamic auto mode
        - doesn't initiate but will use trunking if the other side initiates
      - dynamic desirable
        - the switch will initiate

### STP

- Spanning Tree protocol
- prevents layer 2 loops in switched environments
- 802.1d the OG
- Modern network architecture recommends redundancy like STP or LACP
- RSTP
  - rapid spanning tree
  - supports a single instance of spanning tree
  - converges with much haste
  - assigns roles to ports
  - Edge port
    - Ports directly connected to endpoints and corresponds with portfast port
    - an edge port that receives a BPDU will turn in into a normal spanning tree port
- MSTP
  - multiple spanning tree
  - optimizes PVST by mapping multiple VLANs to the same spanning tree instance
  - has RSTP built in for speedy convergence
  - 802.1w
  - used when you have hundreds or thousands of vlans
- PVST
  - per vlan spanning tree
  - only supported ISL
  - separate 802.1d spanning tree instance for each vlan
    - therefore each vlan has it's own root and own calculations
- PVST +
  - supports ISL and 802.1q
- BPDU
  - Bridge protocol data unit
  - how switches learn about each other
  - sent every 2 seconds
  - used to detect loops for STP
  - contains lots of info like
    - Bridge ID - 8 byte value unique to the switch
  - 3 types of BPDUs
    - Configuration BPDU
      - used by spanning tree to provide information to switches
    - Topology Change BPDU
      - tell a switch of a change
    - Acknowledgment BPDU
      - confirm the receipt of a topology change
  - types of ports in STP
    - Root Port
      - Port closest to root bridge in terms of path cost
    - Designated Port
      - best port to use to get to the root bridge
    - Blocked Ports
      - Backup port
        - port that is blocked because it is receiving more useful BPDUs from the same bridge it is on
      - Alternate Port
        - port that is blocked because it is receiving more useful BPDUs from another bridge
  - BPDU Guard
    - used on access or portfast ports
    - if a BPDU is received from a switch it shuts the port down
    - `spanning tree BPDU guard enable`
- Rapid PVST+
  - rapid per vlan spanning tree plus
  - 1 spanning tree instance per vlan with rapid convergence
  - good for use at approximately 10 vlans
  - default on most cisco switches
- CDP / LLDP
  - cisco discovery protocol
  - uses multicast frames

### NAT 

- a few different kinds of nat that perform similar functions
  - Source NAT
    - Router will translate the source IP of a packet traversing it's interface
      - Static NAT
        - statically configring one to one mappings or private to public ip addresses
        - 
  - Dynamic Nat
    - Router dynamically maps inside local addresses to inside global addresses
    - can use ACLs
    - NAT pool is used to define available inside global addresses
      - if all the inside global addresses get used up you get NAT pool exhaustion
  -  PAT ( AKA NAT overload )
     -  both IPs and Ports will get translated if needed
     -  most widely used for homes and businesses
- inside/outside local/global
  - inside local is usually an endpoint
  - inside global is usually the router's public ip address
  - outside local = ip address of the outside host from the perspective of the local network
    - is usually the server's public ip address
    - is usually the same as outside global network unless destination NAT is used
  - outside global = ip address of the outside host from the perspective of the outside network
    - is usually the server's public ip address
    - is usually the same as outside local network unless destination NAT is used

## IP Routing

### Routing vs Routed protocols

- Routed Protocols
  - ipv4 / ipv6
  - carries user information
- Routing Protocols
  - EIGRP / OSPF / RIP / ISIS / BGP

### Static vs Dynamic Routing

- Static Routing
  - administrator manually enters the route but there's no overhead on network
  - adminstration can be cumbersome

- Dynamic Routing
  - more complex but updates routing tables automatically

### Determing best routes

- static = admin decides
- RIP = hop count
- OSPF = bandwidth ( common in enterprises)
- EIGRP = bandwidth + delay ( common in cisco enterprises )
  - EIGRP is cisco proprietary

### routing terms

- AS ( autonomous system)
  - grouping of networks under a single administrative domain
-IGPs ( interior gateway routing protocols)
  - used within an AS
  - RIP, OSPF, EIGRP
- EGPs ( Exterior Gateway Routing Protocols)
  - used between AS's
- Administrative distance
  - used as a tiebreaker if there's 2 routes that can't agree on a path
  - the lower the administrative distance wins and will be put in routing table
    - a connected interface = 0
    - static route = 1
    - internal EIGRP = 90
    - OSPF = 110
    - RIP = 120
    - unknown = 255
- Classful routing protocols
  - don't advertise subnet mask
  - i.e rip v1
  - not used today because not everything can be a /24 or whatever
- Auto summarization
- classful routing protocols automatically summarize
  - they would set 10.1.1.0 to /8 and 172.16.2.0 to /16 automatically
- Classless routing protocols
  - do advertise subnet mask
  - can do VLSM ( variable length subnet masks)
  - longest matched routes take priority so /24 matches before /16 and not administrative distance

### Types of routing protocols

- Distance Vector
  - determines direction and distance to destination
  - RIP uses hop count for example
  - limited visibility
  - easy to configure
  - uses Bellman-Ford algorithm
  - routers advertise routes as a vector of stiance and direction
  - has multiple features to prevent loops
- Link state
  - complete map of it's network
  - keeps a database of shortest paths
  - OSPF uses bandwidth to calculate best path
  - uses SPF ( shortest path first) algorithm creatbed by djikstra to build topological map
  - more difficult to configure
  - floods the network with LSAs, aka link state advertisements
  - all link state routers create it's topological a toplogoical database
    - contains info on all routers and all links to those routers and the state of the links
-Advanced distance Vector
  - EIGRP
    - power of link state protocols with ease of distance vector protocols
    - cisco proprietary

### Routing Protocols

#### OSPF

- Open Shortest Path First
- Link State routing protocol
  - open standard
- Link = router interface & state = description of an interface and it's relationship to neighboring routers
- topological database / link state database
  - collection of all the link states aggregated
  - Router's create neighbor relationships using unicast or multicast
- uses layer 3 IP protocols
- by default database synchronized every 30 min.
-   - can be broken up into heiarchies
  - breaks the AS into multiple areas
  - uses ABRs area border routers and internal routers and AS border router and backbone routers
  - Packet Types
    - Hello
      - dynamically discovers neighbors
      - default 10 seconds on broadcast ethernet segments
      - dead timer = 4x the hello interval
    - Database Description (DD/DBD)
      - used to exchange versions of each link state advertisment
    - Link State Request (LSR)
      - request for all LSA information
    - link state update (LSU)
      - contains LSAs
      - response from LSRs
    - Link State acknowledgement (LSAck)
      - confirms receipt of an LSU
  - hierarchies
    - area 0 is backbone area
      - all traffic that traverses to different area's will route through the backbone area
    - you should design OSPF by breaking routers up into areas
    - Area border routers (ABR)
      - routers that sit at the border between areas 0 and another area
      - ABRs can summarize routes but must be done carefully
    - Autonomous system border router (ASBR)
      - routers that sit on the border between 2 autonomous systems
    - Internal routers
      - internal to a single OSPF area
    - Designated Routers (DR) & backup Designated Routers
      - DRs 
        - Highest priority
        - default priority is 1
        - ranges from 1 to 255
        - 0 disables the router from being DR
        - listen on multicast address 224.0.0.6
        - only DR receives update
        - DR gets the update and then forwards it to all other routers in segment
        - only DR and BDR have full relationships with all other routers
        - BDR becomes DR if DR fails
  - SPF Algorithm
    - uses a cumulative cost to calculate route
      - default reference bandwidth = 10^8
      - cost = 10^8 / bandwidth
        - 100,000,000 / (10,000,000) or 10mbps = 10
        - 

#### Multicast

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

#### IGMP

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

### Switch Stacking

- switches become 1 logical unit
- STP/CDP/VTP function as 1
- switch stacking often used at access layer
- chassis aggregation used in distribution and core layers
  - used for high availability designs
- stacked switches share a mac address table
- joined together via special cables using different technologies
  - cisco's flexstack 
  - flexstack plus stacking technology

### QOS

#### Policers & Shapers 

- policers
  - policiers can resend traffic or remark traffic to a lower class then resend it
  - can drop traffic
    - will result in TCP Resets or retransmissions
  - good for ingress traffic due to saving bandwidth and CPU resources
- Shapers
  - Will delayor buffer traffic, traffic becomes smoothed
  - a more gentle approach, will introduce delay and jitter when oversubscribed
  - fewer TCP retransmissions
- Policers vs shapers
  - Policers won't delay traffic, shapers will

#### Queueing

- Round Robin Queuing Mechanisms
  - all traffic treated the same way
    - real time traffic could see delays
- Strict Queuing Mechanism
  - High priority traffic like VOIP can starve low priority traffic
- Queuing is only used when there's congestion
- FIFO Queue
  - first in first out
- PQ ( priority Queue)
  - queues = High, Medium, normal, & low
    - High priority queue always goes first
    - medium only goes after high priority is services
    - normal only goes after high and medium are serviced
    - low only goes after high and medium and normal are serviced
- CQ (Custom queuing)
  - 16 queue's serviced in a round robin scheduling fashion
  - provides traffic guarantees
  - voip traffic can get delayed
- Weighted Fair Queueing
  - Weight added to flows based on factors like RSVP or ip precedence
    - better for VOIP and modern networks because of how it quickly handles smaller packets
    - no bandwidth guarantees
- Class-based weighted fair queueing
  - can give traffic classes minimum bandwidth guarantees
    - like VOIP/HTTP/FTP/Video/etc
    - no latency guarantees so only good for data networks 
- Low Latency Queueing
  - classes are put in classes and allows for realtime traffic like voip to be prioritized
  - also allows for minimum bandwidth guarantees and policing so that priority traffic doesn't starve out other traffic
- WRED
  - weighted random early detection
    - used to avoid congestion
    - drops some flows so that certain hosts will slow down. this allows other hosts to speed up so the buffer doesn't get maxed out and then everything slows down at once

### VOIP

- Skinny Call Control Protocol (SCCP)
  - Cisco proprietary terminal control protocol
  - client/server model
- Session initiation protocol (SIP)
  - open standard
  - p2p
  - some processing down by endpoint
  - provides 'presence'

### GRE tunnels

- Generric Routing encapsulation tunneling
  - point to point tunnel (kind of like a vpn)
  - allows the transport of higher level protocols like ipv4 & ipv6
  - has no authentication or encryption
  - allows multicast routing protocols

## Wifi

- Wifi standards
  - wifi 4 aka 802.11n
  - wifi 5 aka 801.11ac
  - wifi 6 aka 802.11 ax
- Radio frequencies
  - 2.4 GHz
    - channels 1-11  and if you use 1 6 and 11 you can avoid overlap and increase throughput
  - 5 GHz
    - The following 5 GHz channels are supported with 20MHz channel width:
      - 36
      - 40
      - 44
      - 48
      - 149
      - 153
      - 157
      - 161
      - 165
- Wifi Security
  - Protected Management Frames (PMF)
    - Provide protection for unicast and multicast management action frames. Unicast management action frames are protected from both eavesdropping and forging, and multicast management action frames are protected from forging
- the technology is more like a half duplex because its doing collision avoidance
- APs in the same geographical area should be on different channels to avoid co-channel contention

## Helpful Commands

### General Commands

- `hostname Router1`
- `ip address 192.168.1.1 255.255.255.0`
- `enable password cisco`
- `conf t -> service password-encryption` ! makes passwords encrypted
- `enable secret cisco123` ! secret password overrides enable password
- `conf t -> line vty 0 4 -> transport input telnet -> password cisco -> login`
- `conf t -> line con 0 -> password cisco`
- `conf t -> line con 0 -> login`
- `no ip domain-lookup`
- `erase startup-config` ! delete startup config from NVRAM when SHTF
- `show protocols` ! shows active network protocols
- `Switch# (config)# interface range gigabitEthernet 1/0/23 - 24 `
- `Switch2#show interfaces status` 
- `Switch(config)#ip host Ohio 195.41.31.11` ! name a name to an ip address
- `Switch# show hosts`
- `Router1# show ip protocols`
- `Router1# show ip ospf database`
- `Router1# show ip ospf neighbor`
- `Router1# show ip ospf interface`
- `Router1# show ip int brief` /line /interface ! filtering on linux and ios
- `Router1#(config) shell processing full` ! lets you use grep or | and maybe other linux commands
- `Router1# copy running-config tftp`

### VLANs

- General
  - `Switch# show vlan`
  - `Switch# show vlan 1`
  - `Switch# show vlan brief`
  - `Switch# vlan database` 
  - `Switch# show vtp status`



- Access Ports
  - `Switch(config-if)# switchport mode access`
  - `Switch(config-if)# switchport nonegotiate` ! disables DTP (Dynamic Trunking protocol)
  - `Switch(config-if)# switchport access vlan 69`
  - `Switch(config-if)# switchport voice vlan 666`
- Trunk Ports
  - `Switch(config-if)# switchport trunk encapsulation dot1q`
  - `Switch(config-if)# switchport mode trunk`
  - `Switch(config-if)# switchport trunk allowed vlan 69,100-200`
  - `Switch(config-if)# switchport trunk native vlan 1`
  - `Router1(config-subif)# encapsulation dot1q 2 ` ! used for ROAS & intervlan routing. in this example it allows subinterface to use dot1q trunking to see vlan ID 2
- VTP
  - `Switch(config)vtp domain ccna`
  - `Switch(config)vtp mode server`
  - `Switch(config)vtp mode client`
  - `Switch# show vtp status`

### STP/CDP/LLDP/Etherchannel

- STP
  - `Switch(config)spanning-tree portfast edge bpduguard`
  - `Switch(config-if)#spanning-tree portfast`
  - `Core2(config-if)#spanning-tree link-type point-to-point `
- CDP
  - `Switch#show cdp neighbors`
  - `Router#show cdp`
  - `Router#show cdp entry Router1`
  - `Router#show cdp interface`
  - `Router#show cdp traffic`
  - `Switch(config) cdp run`
- LLDP
  - `Switch#show lldp`
  - `Switch#show lldp neighbors detail`
- Etherchannel
  - `Core2(config)#int range gigabitEthernet 1/0/23 - 24`
  - `Core2(config-if-range)#switchport mode trunk`
  - `Core2(config-if-range)#channel-group 1 mode active`
  - `Core2#show etherchannel summary`
  - `Core2(config-if-range)#no switchport` ! convert switchtport to routed port
- LACP
  - `Switch1(config)#int range gigabitEthernet 1/0/23 - 24`
  - `Switch1(config-if-range)#channel-protocol lacp`
  - `Switch1(config-if-range)#channel-group 1 mode passive`
  - `Switch1(config-if-range)#channel-group 1 mode active`
  - `Switch1#show interfaces port-channel 1`
  - `Switch1#show etherchannel port-channel`
  - `Switch1#show etherchannel summary`
  - `Switch1(config)#lacp system priority 100`
  - `Switch1(config-if)#lacp port-priority 100`



### IP

- DHCP
- ` R1(config)# service dhcp`
- ` R1(config)# ip dhcp excluded-address 10.1.10.1 10.1.10.10 `
- ` R1(config)# ip dhcp pool vlan10 `
- ` R1(dhcp-config)# network 10.1.10.0 255.255.255.0 `
- ` R1(dhcp-config)# default-router 10.1.10.1 `
- ` R1(dhcp-config)# dns-server 10.1.1.254 `
- ` R1(dhcp-config)# lease 2 ` ! set lease to 2 days
- ` R1(dhcp-config)# domain-name brandonvshort.com`
- ` R1# show ip dhcp binding` ! show DHCP clients
- ` R1# show ip dhcp server statistics `
- ` R2(config-if)#ip address dhcp` ! tell interface to pull IP from dhcp
- ` R2# show dhcp lease`
- ` R2# show dhcp server`
- ` S1(config-if)# ip helper-address 10.1.1.254`

- DNS
- ` R1# configure terminal `
- ` R1(config)# ip dns server `
- ` R1(config)# ip domain-lookup `
- ` R1(config)# ip name-server 8.8.8.8 `

### HSRP (hot standby router protocol)

- ` Core1(config-if)# standby 1 ip 10.1.10.254 `
- ` Core1(config-if)# standby 1 priority 200 `
- ` Core1(config-if)# standby 1 preempt `
- `Core1# show standby`


### NTP

- ` R1# show clock `
- ` R1(config)# ntp server 10.1.1.201 `
- `R1# clock set 6:40:00 30 NOV 2021`
- ` R1# clock timezone EST -5 `
- ` R1# clock summer-time american_summer recurring last sun MAR 1:00 last SUN Oct 1:00 `

### SYSLOG

- `R1(config)# logging host 10.1.1.200`
- ` R1(config)# service timestamps log datetime msec `

### SPAN ports

- `S1(config)# monitor session 1 source vlan 1 both`
- ` S1(config)# monitor session 1 destination interface fastEthernet 1/0/5 `
- ` S1(config)# monitor session 1 destination interface fastEthernet 1/0/5 ingress untagged vlan 1 `
- `S1# show monitor`
- `S1(config)# no monitor session 1`

### NAT

- `R2(config)#ip nat inside source static 10.1.1.1 8.1.1.5` 
- `R2# show ip nat translations`
- `R2# show ip nat statistics`


### Routing

- `R1#show ip route`
- `S1(config)# ip route 1.1.1.1 255.255.255.255 10.1.1.254 `
- `R1(config)# ip route 0.0.0.0 0.0.0.0 192.168.2.1 ` ! a more permissive static route than above
- `S1(config)# ip routing`
- `S1(config)# ip default-gateway 10.1.1.254 `

#### RIPv2

- `R1(config)#router rip`
- `R1(config-router)#version 2`
- `R1(config-router)#network 192.168.1.0`
- `R1(config-router)#network 192.168.2.0`
- `R1(config-router)#no auto-summary` ! In case something like a 172.16.0.0/16 would cause conflicts

#### EIGRP

- `IntRouter(config)#router eigrp 100`
- `IntRouter(config-router)# network 10.1.1.0 0.0.0.255`
- `IntRouter(config-router)# no auto-summary`
- `IntRouter# show ip eigrp interfaces`

#### OSPF

- `Router1(config-router)#ip ospf 1`
- `Router1(config-router)#network 1.1.1.0 0.0.0.255` ! or 
- `Router1(config-router)#network 1.1.1.1 0.0.0.0` ! or 
- `Router1(config-router)#interface g0/0` ! programming interface & not network
- `Router1(config-if)# ip ospf 1 area 0` ! programming interface & not network
- `Router1# show ip protocols` ! shows active routing protocols
- `Router1# show ip ospf database` ! shows info about OSPF Link state database
- `Router1# show ip ospf neighbor` ! shows info about OSPF neighbrs
- `Router1# show ip ospf interface` ! shows info about OSPF interface info
- `Router1(config)#interface loopback 0` ! loopbacks are good to program so they'll be used for router ID in ospf 

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

[David Bombals binary/decimal/subnetting] quizzes(<https://davidbombal.com/free-quiz/>)

[Network Chuck's sweet Fiber video](https://youtu.be/E3DEJ7odWq0)

## Shortcuts
- CTRL + A = moves cursor to beginning of command line
- CTRL + E = moves cursor to end of command line
- CTRL + Shift + 6 = interrupt command like ping
- CTRL + Shift + 6 then X = hide telnet sessions without breaking it