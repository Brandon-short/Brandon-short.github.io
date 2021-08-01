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
  - [Networking Basics](#networking-basics-1)
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
  - Wireless Lan Controller
    - Used to manage multiple Acess Points


## TCP/IP Model
- Newest Version of CCNA is using hybrid tcp/ip model:
  - 5. Application
        - PDU = application data
  - 4. Transport
        - PDU = Segments
  - 3. Network
        - PDU = Packets
  - 2. Data Link
        - PDU = Frames
        - if Type field = 0x800 that indicates ipv4
        - if Type field = 0x806 that indicates arp
  - 1. Physical
        - PDU = Bits

### Important ports to remember & their protocol
|Service   	|Port      	|Protocol   |
|-----------|-----------|-----------|
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
|Exponent|2^7| 2^6| 2^5| 2^4| 2^3| 2^2| 2^1| 2^0|
|---|---|---|---|---|---|---|---|---|
|Binary|1|1|1|1|1|1|1|1|
|Decimal |128|64|32|16|8|4|2|1|

## Hexadecimal

## IP Addressing

## Networking Basics



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