# 🚀 NetSimX Implementation Guide

## Overview
This is my step-by-step guide for implementing the entire CMPG 325 Computer Networks project. I've broken it down into two main phases with clear sections so I can follow along easily and not miss anything important.

---

## 📋 Quick Project Summary
- **Total Worth**: 100 marks
- **Due Date**: October 13, 2025
- **Tool**: Cisco Packet Tracer (latest version)
- **Deliverables**: 6 .pkt files + 15-30 minute video demonstration

---

# 🏗️ PHASE 1: TOPOLOGY IMPLEMENTATION (60% - 60 marks)

This phase is where I build all my network topologies in Cisco Packet Tracer. Each topology is worth different marks based on complexity.

## Section 1: Bus Topology (8 marks)
**Estimated Time**: 2-3 hours

### What I'm Building
- 5 PCs connected through a central hub (simulating bus cable)
- Simple network with basic connectivity
- IPv4 addressing scheme

### Step-by-Step Implementation

#### 1. Physical Setup
```
1. Open Cisco Packet Tracer
2. Drag 5 Generic PCs from End Devices
3. Name them: BUS-PC01, BUS-PC02, BUS-PC03, BUS-PC04, BUS-PC05
4. Drag 1 Hub-PT from Network Devices
5. Connect all PCs to hub using straight-through cables
6. Verify green dots on all connections
```

#### 2. IP Configuration
| Device | IP Address | Subnet Mask | Gateway |
|--------|------------|-------------|---------|
| BUS-PC01 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| BUS-PC02 | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| BUS-PC03 | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 |
| BUS-PC04 | 192.168.1.13 | 255.255.255.0 | 192.168.1.1 |
| BUS-PC05 | 192.168.1.14 | 255.255.255.0 | 192.168.1.1 |

#### 3. Testing
- Ping from PC01 to all other PCs
- Use simulation mode to watch packets travel
- Document results in testing-results.md

#### 4. Save File
Save as: `topologies/01-bus-topology/bus-topology.pkt`

---

## Section 2: Mesh Topology (12 marks)
**Estimated Time**: 4-5 hours

### What I'm Building
- 4 routers in full mesh configuration (every router connects to every other)
- Multiple paths for redundancy
- OSPF routing protocol

### Step-by-Step Implementation

#### 1. Physical Setup
```
1. Drag 4 Router-PT devices
2. Name them: MESH-R1, MESH-R2, MESH-R3, MESH-R4
3. Connect every router to every other router (6 connections total)
   - R1 connects to R2, R3, R4
   - R2 connects to R3, R4 (already connected to R1)
   - R3 connects to R4 (already connected to R1, R2)
4. Use serial cables for WAN connections
```

#### 2. IP Configuration for Router Interfaces
| Connection | Router | Interface | IP Address | Subnet |
|------------|--------|-----------|------------|---------|
| R1-R2 | R1 | S0/0/0 | 10.1.12.1 | /30 |
| R1-R2 | R2 | S0/0/0 | 10.1.12.2 | /30 |
| R1-R3 | R1 | S0/0/1 | 10.1.13.1 | /30 |
| R1-R3 | R3 | S0/0/0 | 10.1.13.2 | /30 |
| R1-R4 | R1 | S0/1/0 | 10.1.14.1 | /30 |
| R1-R4 | R4 | S0/0/0 | 10.1.14.2 | /30 |
| R2-R3 | R2 | S0/0/1 | 10.1.23.1 | /30 |
| R2-R3 | R3 | S0/0/1 | 10.1.23.2 | /30 |
| R2-R4 | R2 | S0/1/0 | 10.1.24.1 | /30 |
| R2-R4 | R4 | S0/0/1 | 10.1.24.2 | /30 |
| R3-R4 | R3 | S0/1/0 | 10.1.34.1 | /30 |
| R3-R4 | R4 | S0/1/0 | 10.1.34.2 | /30 |

#### 3. OSPF Configuration
Configure on each router:
```
router ospf 1
network 10.1.0.0 0.0.255.255 area 0
```

#### 4. Testing
- Check routing tables on all routers
- Traceroute between different routers
- Simulate link failure to test redundancy

#### 5. Save File
Save as: `topologies/02-mesh-topology/mesh-topology.pkt`

---

## Section 3: Star Topology (10 marks)
**Estimated Time**: 3-4 hours

### What I'm Building
- Central switch with 6 PCs connected
- VLANs for network segmentation
- Basic switch management

### Step-by-Step Implementation

#### 1. Physical Setup
```
1. Drag 1 Switch (2960) from Network Devices
2. Drag 6 Generic PCs from End Devices
3. Name PCs: STAR-PC01 through STAR-PC06
4. Connect all PCs to switch using straight-through cables
5. Note which port each PC connects to
```

#### 2. VLAN Configuration
| VLAN | Name | Ports | Purpose |
|------|------|-------|---------|
| 10 | Sales | Fa0/1-2 | Sales Department |
| 20 | IT | Fa0/3-4 | IT Department |
| 30 | Guest | Fa0/5-6 | Guest Access |

#### 3. IP Configuration
| Device | VLAN | IP Address | Subnet Mask | Gateway |
|--------|------|------------|-------------|---------|
| STAR-PC01 | 10 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| STAR-PC02 | 10 | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| STAR-PC03 | 20 | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |
| STAR-PC04 | 20 | 192.168.20.11 | 255.255.255.0 | 192.168.20.1 |
| STAR-PC05 | 30 | 192.168.30.10 | 255.255.255.0 | 192.168.30.1 |
| STAR-PC06 | 30 | 192.168.30.11 | 255.255.255.0 | 192.168.30.1 |

#### 4. Switch Configuration Commands
```
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name Sales
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# name IT
Switch(config-vlan)# exit
Switch(config)# vlan 30
Switch(config-vlan)# name Guest
Switch(config-vlan)# exit

Switch(config)# interface fastethernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

[Repeat for all ports...]
```

#### 5. Testing
- Ping within same VLAN (should work)
- Ping between different VLANs (should fail - this is correct)
- Check VLAN assignments

#### 6. Save File
Save as: `topologies/03-star-topology/star-topology.pkt`

---

## Section 4: Ring Topology (10 marks)
**Estimated Time**: 3-4 hours

### What I'm Building
- 4 switches connected in a ring formation
- Spanning Tree Protocol (STP) to prevent loops
- PCs connected to each switch

### Step-by-Step Implementation

#### 1. Physical Setup
```
1. Drag 4 Switches (2960) from Network Devices
2. Name them: RING-SW1, RING-SW2, RING-SW3, RING-SW4
3. Connect in ring: SW1→SW2→SW3→SW4→SW1 using trunk cables
4. Add 2 PCs to each switch
5. Name PCs: RING-PC01, RING-PC02, etc.
```

#### 2. Ring Connections
| Connection | Switch 1 Port | Switch 2 Port | Cable Type |
|------------|---------------|---------------|------------|
| SW1-SW2 | Fa0/24 | Fa0/23 | Straight-through |
| SW2-SW3 | Fa0/24 | Fa0/23 | Straight-through |
| SW3-SW4 | Fa0/24 | Fa0/23 | Straight-through |
| SW4-SW1 | Fa0/24 | Fa0/23 | Straight-through |

#### 3. Spanning Tree Configuration
```
Switch> enable
Switch# configure terminal
Switch(config)# spanning-tree mode pvst
Switch(config)# spanning-tree portfast default
```

#### 4. IP Configuration
| Device | IP Address | Subnet Mask | Gateway |
|--------|------------|-------------|---------|
| RING-PC01 | 192.168.4.10 | 255.255.255.0 | 192.168.4.1 |
| RING-PC02 | 192.168.4.11 | 255.255.255.0 | 192.168.4.1 |
| RING-PC03 | 192.168.4.12 | 255.255.255.0 | 192.168.4.1 |
| RING-PC04 | 192.168.4.13 | 255.255.255.0 | 192.168.4.1 |
| RING-PC05 | 192.168.4.14 | 255.255.255.0 | 192.168.4.1 |
| RING-PC06 | 192.168.4.15 | 255.255.255.0 | 192.168.4.1 |
| RING-PC07 | 192.168.4.16 | 255.255.255.0 | 192.168.4.1 |
| RING-PC08 | 192.168.4.17 | 255.255.255.0 | 192.168.4.1 |

#### 5. Testing
- Check spanning tree status: `show spanning-tree`
- Disconnect one link to test redundancy
- Verify all PCs can communicate

#### 6. Save File
Save as: `topologies/04-ring-topology/ring-topology.pkt`

---

## Section 5: Extended Star Topology (10 marks)
**Estimated Time**: 4-5 hours

### What I'm Building
- Core switch connected to multiple access switches
- Hierarchical network design
- Inter-VLAN routing

### Step-by-Step Implementation

#### 1. Physical Setup
```
1. Drag 1 Multilayer Switch (3560) as core switch
2. Drag 3 Access Switches (2960)
3. Name them: CORE-SW, ACCESS-SW1, ACCESS-SW2, ACCESS-SW3
4. Connect each access switch to core switch
5. Add 3-4 PCs to each access switch
```

#### 2. VLAN Strategy
| VLAN | Name | Access Switch | Purpose |
|------|------|---------------|---------|
| 100 | Management | All | Switch Management |
| 10 | Floor1 | ACCESS-SW1 | First Floor Users |
| 20 | Floor2 | ACCESS-SW2 | Second Floor Users |
| 30 | Floor3 | ACCESS-SW3 | Third Floor Users |

#### 3. Core Switch Configuration
```
Switch> enable
Switch# configure terminal
Switch(config)# ip routing
Switch(config)# vlan 10
Switch(config-vlan)# name Floor1
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# name Floor2
Switch(config-vlan)# exit
Switch(config)# vlan 30
Switch(config-vlan)# name Floor3
Switch(config-vlan)# exit

Switch(config)# interface vlan 10
Switch(config-if)# ip address 192.168.10.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

Switch(config)# interface vlan 20
Switch(config-if)# ip address 192.168.20.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

Switch(config)# interface vlan 30
Switch(config-if)# ip address 192.168.30.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit
```

#### 4. Testing
- Ping between different VLANs (should work through core switch)
- Check routing table on core switch
- Test inter-VLAN communication

#### 5. Save File
Save as: `topologies/05-extended-star/extended-star-topology.pkt`

---

## Section 6: Hybrid Integration (10 marks)
**Estimated Time**: 6-8 hours

### What I'm Building
- Combination of all previous topologies
- Routers connecting different topology segments
- Complete enterprise network

### Step-by-Step Implementation

#### 1. Network Segments
```
1. Bus Segment: Legacy devices (192.168.1.0/24)
2. Mesh Core: High-availability routing (10.1.0.0/16)
3. Star Access: Department networks (192.168.10-30.0/24)
4. Ring Backbone: Campus connectivity (192.168.4.0/24)
5. Extended Star: Main office (192.168.50-52.0/24)
```

#### 2. Integration Points
- Router connecting Bus to Mesh core
- Router connecting Star to Mesh core
- Router connecting Ring to Mesh core
- Router connecting Extended Star to Mesh core

#### 3. Routing Protocol
Configure OSPF on all routers to share routing information:
```
router ospf 1
network 192.168.0.0 0.0.255.255 area 0
network 10.1.0.0 0.0.255.255 area 0
```

#### 4. Testing
- Ping from any device to any other device
- Traceroute to see path selection
- Test redundancy by disabling links

#### 5. Save File
Save as: `topologies/06-hybrid-integration/hybrid-integration.pkt`

---

# 🖥️ PHASE 2: NETWORK SERVICES (40% - 40 marks)

This phase is where I configure network services. I only need to implement ONE service, but I should choose carefully to maximize marks.

## Service Option 1: Email Server (Recommended - 40 marks)
**Estimated Time**: 8-10 hours

### Why I'm Choosing Email
- Worth full 40 marks
- Demonstrates multiple protocols (SMTP, POP3, IMAP)
- Shows DNS integration
- Realistic enterprise service

### What I'm Building
- Email server with SMTP, POP3, and IMAP
- DNS server for mail routing
- Multiple email accounts
- Email clients for testing

### Step-by-Step Implementation

#### 1. Server Setup
```
1. Drag Server-PT from End Devices
2. Name it: EMAIL-SERVER
3. Connect to network (use Star topology network)
4. Configure IP: 192.168.100.10
5. Configure DNS: 192.168.100.30
```

#### 2. DNS Configuration First
```
1. Add another Server-PT for DNS
2. Name it: DNS-SERVER
3. IP: 192.168.100.30
4. Configure DNS service:
   - Add A record: mail.netsimx.local → 192.168.100.10
   - Add MX record: netsimx.local → mail.netsimx.local
```

#### 3. Email Server Configuration
```
1. Click on EMAIL-SERVER
2. Go to Services tab
3. Enable SMTP:
   - Domain name: netsimx.local
   - Turn service ON
4. Enable POP3:
   - Turn service ON
5. Enable IMAP (if available):
   - Turn service ON
```

#### 4. Create Email Accounts
```
1. In EMAIL-SERVER Services tab
2. Go to Email section
3. Add users:
   - admin@netsimx.local (password: admin123)
   - tshepang@netsimx.local (password: student123)
   - user1@netsimx.local (password: user123)
   - support@netsimx.local (password: support123)
```

#### 5. Configure Email Clients
```
1. On each PC, configure email client:
   - Incoming mail server: 192.168.100.10
   - Outgoing mail server: 192.168.100.10
   - Account: username@netsimx.local
   - Password: (respective password)
```

#### 6. Testing Checklist
- [ ] Send email from tshepang@netsimx.local to admin@netsimx.local
- [ ] Reply to email
- [ ] Send email with attachment (if supported)
- [ ] Test POP3 access
- [ ] Test IMAP access (if available)
- [ ] Verify DNS resolution of mail.netsimx.local

### Save Files
- Main topology with email server: `network-services/email-server-config/email-topology.pkt`
- Documentation in: `network-services/email-server-config/`

---

## Alternative Service Options

### Web Server (35 marks)
- HTTP/HTTPS services
- Multiple websites
- DNS integration
- Less complex than email

### DHCP Server (30 marks)
- Automatic IP assignment
- Multiple scopes
- Easier to configure
- Lower marks potential

---

# 📹 PHASE 3: VIDEO DEMONSTRATION (Bonus marks)

## Video Structure (15-30 minutes)

### Introduction (2-3 minutes)
- "Hi, I'm Tshepang and this is my CMPG 325 Computer Networks project"
- Overview of what I'll demonstrate
- Brief explanation of NetSimX

### Topology Demonstrations (15-20 minutes)
For each topology (3-4 minutes each):
1. Show the physical layout
2. Explain the key concepts
3. Demonstrate connectivity (ping tests)
4. Show unique features (VLANs, routing tables, etc.)

### Network Service Demo (5-8 minutes)
- Show email server configuration
- Demonstrate sending/receiving emails
- Show DNS resolution
- Explain how services integrate with topologies

### Conclusion (1-2 minutes)
- Summary of what I learned
- Challenges faced and overcome
- Future improvements

## Recording Tips
- Use OBS Studio or Camtasia for screen recording
- Speak clearly and at moderate pace
- Show Packet Tracer simulation mode
- Zoom in on important configurations
- Practice before final recording

---

# 🎯 Implementation Timeline

## Week 1: Foundation (Bus, Star, Ring)
- Day 1-2: Bus topology
- Day 3-4: Star topology  
- Day 5-6: Ring topology
- Day 7: Testing and documentation

## Week 2: Advanced Topologies
- Day 1-3: Mesh topology
- Day 4-5: Extended Star topology
- Day 6-7: Start Hybrid integration

## Week 3: Integration and Services
- Day 1-2: Complete Hybrid integration
- Day 3-5: Email server implementation
- Day 6-7: Testing and troubleshooting

## Week 4: Final Polish
- Day 1-2: Video demonstration recording
- Day 3-4: Final testing and documentation
- Day 5-6: Upload to GitHub and submit
- Day 7: Buffer for any issues

---

# 📚 Quick Reference

## Essential Cisco Commands
```bash
# Basic router configuration
Router> enable
Router# configure terminal
Router(config)# interface serial0/0/0
Router(config-if)# ip address 10.1.1.1 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)# exit

# OSPF routing
Router(config)# router ospf 1
Router(config-router)# network 10.1.1.0 0.0.0.3 area 0

# Switch VLAN configuration
Switch(config)# vlan 10
Switch(config-vlan)# name Sales
Switch(config-vlan)# exit
Switch(config)# interface fastethernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
```

## IP Subnetting Quick Guide
- /30 = 255.255.255.252 (4 IPs, 2 usable) - Point-to-point links
- /24 = 255.255.255.0 (256 IPs, 254 usable) - Standard LAN
- /26 = 255.255.255.192 (64 IPs, 62 usable) - Small department

## Troubleshooting Checklist
1. Check physical connections (green dots)
2. Verify IP configurations
3. Test with ping and traceroute
4. Check routing tables
5. Verify VLAN assignments
6. Use simulation mode for packet analysis

---

**Remember**: This is my comprehensive guide. I should follow it step by step, take breaks between sections, and test everything thoroughly. The key to success is not rushing and documenting everything as I go!