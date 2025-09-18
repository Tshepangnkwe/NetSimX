# 🚀 NetSimX Implementation Guide

This is my complete step-by-step guide for the CMPG 325 Computer Networks project. Everything I need is here.

## 📋 Project Summary
- **Worth**: 100 marks total
- **Due**: October 13, 2025  
- **Tool**: Cisco Packet Tracer
- **Files**: 6 .pkt files + video demo

---

# 🏗️ PHASE 1: NETWORK TOPOLOGIES (60 marks)

## 1. Bus Topology (8 marks) - 2 hours

**What I'm building**: 5 PCs connected through a hub (simulating bus backbone)

### Setup Steps
1. Open Packet Tracer
2. Add 5 Generic PCs: BUS-PC01 through BUS-PC05
3. Add 1 Hub-PT device
4. Connect all PCs to hub with straight-through cables
5. Configure IP addresses:

| Device | IP Address | Subnet Mask | Gateway |
|--------|------------|-------------|---------|
| BUS-PC01 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| BUS-PC02 | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| BUS-PC03 | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 |
| BUS-PC04 | 192.168.1.13 | 255.255.255.0 | 192.168.1.1 |
| BUS-PC05 | 192.168.1.14 | 255.255.255.0 | 192.168.1.1 |

### Testing
- Ping between all PCs
- Use simulation mode to watch packets
- Save as: `packet-tracer-files/01-bus-topology.pkt`

---

## 2. Mesh Topology (12 marks) - 4 hours

**What I'm building**: 4 routers in full mesh with OSPF routing

### Setup Steps
1. Add 4 Router-PT devices: MESH-R1, MESH-R2, MESH-R3, MESH-R4
2. Connect every router to every other router (6 connections total)
3. Configure interfaces with /30 subnets:

| Connection | Router 1 | Interface | IP | Router 2 | Interface | IP |
|------------|----------|-----------|----|---------|-----------|----|
| R1-R2 | R1 | S0/0/0 | 10.1.12.1/30 | R2 | S0/0/0 | 10.1.12.2/30 |
| R1-R3 | R1 | S0/0/1 | 10.1.13.1/30 | R3 | S0/0/0 | 10.1.13.2/30 |
| R1-R4 | R1 | S0/1/0 | 10.1.14.1/30 | R4 | S0/0/0 | 10.1.14.2/30 |
| R2-R3 | R2 | S0/0/1 | 10.1.23.1/30 | R3 | S0/0/1 | 10.1.23.2/30 |
| R2-R4 | R2 | S0/1/0 | 10.1.24.1/30 | R4 | S0/0/1 | 10.1.24.2/30 |
| R3-R4 | R3 | S0/1/0 | 10.1.34.1/30 | R4 | S0/1/0 | 10.1.34.2/30 |

4. Configure OSPF on all routers:
```
router ospf 1
network 10.1.0.0 0.0.255.255 area 0
```

### Testing
- Check routing tables: `show ip route`
- Test connectivity between all routers
- Save as: `packet-tracer-files/02-mesh-topology.pkt`

---

## 3. Star Topology (10 marks) - 3 hours

**What I'm building**: Central switch with 6 PCs in different VLANs

### Setup Steps
1. Add 1 Switch-2960 and 6 Generic PCs
2. Connect all PCs to switch
3. Configure VLANs:

| VLAN | Name | Ports | IP Range |
|------|------|-------|----------|
| 10 | Sales | Fa0/1-2 | 192.168.10.0/24 |
| 20 | IT | Fa0/3-4 | 192.168.20.0/24 |
| 30 | Guest | Fa0/5-6 | 192.168.30.0/24 |

4. Switch configuration:
```
vlan 10
name Sales
exit
vlan 20  
name IT
exit
vlan 30
name Guest
exit

interface fastethernet0/1
switchport mode access
switchport access vlan 10
```

### Testing
- Ping within same VLAN (should work)
- Ping between VLANs (should fail)
- Save as: `packet-tracer-files/03-star-topology.pkt`

---

## 4. Ring Topology (10 marks) - 3 hours

**What I'm building**: 4 switches in ring with Spanning Tree Protocol

### Setup Steps
1. Add 4 Switch-2960 devices: RING-SW1 through RING-SW4
2. Connect in ring: SW1→SW2→SW3→SW4→SW1
3. Add 2 PCs per switch (8 PCs total)
4. Configure all PCs in 192.168.4.0/24 network
5. Enable Spanning Tree:
```
spanning-tree mode pvst
```

### Testing
- Check spanning tree: `show spanning-tree`
- Test redundancy by disconnecting one link
- Save as: `packet-tracer-files/04-ring-topology.pkt`

---

## 5. Extended Star (10 marks) - 4 hours

**What I'm building**: Core switch connected to 3 access switches with inter-VLAN routing

### Setup Steps
1. Add 1 Multilayer Switch-3560 (core) and 3 Switch-2960 (access)
2. Connect each access switch to core switch
3. Add 3-4 PCs per access switch
4. Configure VLANs and routing on core switch:

```
ip routing
vlan 10
name Floor1
exit
vlan 20
name Floor2  
exit
vlan 30
name Floor3
exit

interface vlan 10
ip address 192.168.10.1 255.255.255.0
no shutdown
```

### Testing
- Ping between different VLANs through core switch
- Save as: `packet-tracer-files/05-extended-star.pkt`

---

## 6. Hybrid Integration (10 marks) - 6 hours

**What I'm building**: All previous topologies connected via routers

### Setup Steps
1. Open all previous topology files
2. Add routers to connect each topology segment
3. Configure OSPF to share routes between all segments
4. Create one large integrated network

### Testing
- Ping from any device to any other device
- Verify routing tables show all networks
- Save as: `packet-tracer-files/06-hybrid-integration.pkt`

---

# 📧 PHASE 2: EMAIL SERVER (40 marks)

## What I'm Building
Complete email system with SMTP, POP3, and DNS integration

### Setup Steps

1. **Add DNS Server**
   - IP: 192.168.100.30
   - Add A record: mail.netsimx.local → 192.168.100.10
   - Add MX record: netsimx.local → mail.netsimx.local

2. **Add Email Server**
   - IP: 192.168.100.10
   - Enable SMTP service (domain: netsimx.local)
   - Enable POP3 service
   - Create email accounts:
     - admin@netsimx.local
     - tshepang@netsimx.local
     - user1@netsimx.local
     - support@netsimx.local

3. **Configure Email Clients**
   - Set incoming/outgoing server to 192.168.100.10
   - Test sending and receiving emails

### Testing
- Send email between accounts
- Verify DNS resolution
- Save as: `packet-tracer-files/email-server.pkt`

---

# 📹 VIDEO DEMONSTRATION

## Structure (15-30 minutes)
1. **Introduction** (2 min) - Project overview
2. **Topology Demos** (20 min) - Show each topology working
3. **Email Server** (5 min) - Demonstrate email functionality
4. **Conclusion** (2 min) - What I learned

## Recording Tips
- Use simulation mode to show packet flow
- Speak clearly and explain what you're showing
- Include ping tests and configuration screenshots

---

# 🎯 QUICK REFERENCE

## Essential Commands
```bash
# Router Interface Config
interface serial0/0/0
ip address 10.1.1.1 255.255.255.252
no shutdown

# OSPF Config
router ospf 1
network 10.1.1.0 0.0.0.3 area 0

# Switch VLAN Config
vlan 10
name Sales
interface fastethernet0/1
switchport access vlan 10

# Testing Commands  
ping 192.168.1.1
show ip route
show spanning-tree
```

## IP Subnetting
- /30 = 255.255.255.252 (Point-to-point links)
- /24 = 255.255.255.0 (Standard LANs)

## Troubleshooting
1. Check physical connections (green dots)
2. Verify IP configurations
3. Test with ping
4. Check routing tables
5. Use simulation mode

---

**File Locations:**
- All .pkt files: `packet-tracer-files/` folder
- Screenshots: `screenshots/` folder  
- IP tables: `documentation/ip-addresses.md`

**Remember:** Take your time, test everything, and document as you go!