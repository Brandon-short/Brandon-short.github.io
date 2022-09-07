---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
title: fortiswitch
permalink: /fortiswitch/
---
# Fortiswitch Notes

- [Fortiswitch Notes](#fortiswitch-notes)
  - [Fortiswitch Basics](#fortiswitch-basics)
    - [Fortiswitch Models](#fortiswitch-models)
    - [Management Modes](#management-modes)
    - [Overview](#overview)
    - [Misc](#misc)
    - [Helpful CLI commands](#helpful-cli-commands)


## Fortiswitch Basics

- operates @ layer 2 
- layer 3 static routing is support on all models
  - Some models support dynamic routing but will require an advanced features license
- Most commonly managed by a fortigate via fortilink and this doesn't require any additional licensing
- will integrate with fortinet security fabric

### Fortiswitch Models

- Secure Access Models
  - Entry Level
    - 100 series
      - 8-48 1g POE+ capable ports
      - no redundant PSUs
      - small to mid level
  - Mid Range
    - 200 series
      - 24-48 1g POE+ capable ports
      - redundant PSUs
      - small to mid level
  - Premium
    - 400 series
      - 24-48 1g POE+ & UPOE capable ports
      - redudant PSUs
      - enterprise/secure sd-branch/campus
  - Aggregation
    - 500 series
      - 24-48 1g POE+ capable ports
      - 4 10g SFP+ and 2 40G QSFP+ uplinks
      - split port support
      - redundant PSUs
      - aggregation layer/campus
- Datacenter Models
  - 1000 series
    - top of rack/data center applciation
    - 24-48 10g SFP+ ports w/up to 4 QSFP28 100G uplinks or 6 40G QSFP+ 
    - redundant & hot swappable PSUs
    - no poe support
  - 3000 series
    - top of rack/data center aplications
    - 32  40G QSFP+ or 100GE QSFP28 ports
    - redudnant & hot swappable PSUs
    - no poe support
- Rugged Models
  - 112D-POE
    - 8 1GB RJ45 POE+ capable ports 
    - 4 1G SFP ports
    - passive cooling
    - redundant PSUs
    - IP30 rating protection
  - 124D Switch
    - 16 1g RJ45 ports & 4 1g sfp ports
    - 8 shared media interfaces
    - passive cooling 
    - redundant power inputs
    - ip30 rating protection
  
### Management Modes

- Standalone
  - no fortigate required
  - managed via own Fortiswitch CLI or gui
  - factory default mode
- Managed (by fortigate) Switch Mode
  - managed via fortigate GUI or CLI
  - fortigate acts like switch controller
  - switch is connected to fortiLink interface
- Fortiswitch Cloud
  - requires internet access

### Overview

- Managed Fortiswitches connect directly or indirectly to Fortilink interfaces
- intra-VLAN traffic is handled by Fortiswitch Stack and any other traffic is handled by fortigate
- Stack is connecto to the fortilink interface so it functions like a RoaS topology
- Fortilink interfaces
  - by default it's empty LAG interface and interface members must be added
  - by default uses 169.254.1.1/24 but this isn't routeable so can be changed to something routeable
  - fortilink split interface
    - useful when connecting two or more switches ( one uplink per switch) when the switches don't support MCLAG or isn't configured yet
- MGMT protocols
  - Fortilink
    - used for discovery and heartbeats
  - LLDP
    - alternative to fortiswitch discovery
    - used for auto-isl
  - CAPWAP
    - does switch authentication and authorization
    - also used used for heartbeats
    - alternative & legacy method for fortigate to send upgrades to fortiswitch
  - DHCP/DNS/NTP/HTTPS/SSH
  - Default VLANs
    - 1 default fortilink vlan
    - 4093 quarantine
    - 4091 voice
    - 4090 video
    - 4092 rspan
    - 4089 onboarding


### Misc

- for a fortigate to discover and manage a fortiswitch it must be compatible
  - [compatability matrix](https://fortinetweb.s3.amazonaws.com/docs.fortinet.com/v2/attachments/d756e8a9-6d2d-11e9-81a4-00505692583a/FortiLinkCompatibility.pdf) 
- Make sure the switch controller feature is enabled in the feature visibility
- since you cant use gui to program a firewall policy to allow access to fortilink you must use cli
- making changes directly on managed fortiswitch is not recommneded
- 

### Helpful CLI commands

- `execute switch-controller get-conn-status`
- 
