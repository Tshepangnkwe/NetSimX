# My NetSimX Video Demonstration Script

## CMPG 325 Computer Networks Project - My Video Presentation

### Total Duration: 15-30 minutes
### Part I: My Topology Overview (10-15 minutes)
### Part II: My Network Services Demo (5-15 minutes)

---

## My Pre-Recording Checklist
- [ ] All my topology .pkt files working correctly
- [ ] All my network services operational
- [ ] Screen recording software ready
- [ ] Audio testing completed
- [ ] Cisco Packet Tracer updated to latest version
- [ ] All my screenshots taken and organized

---

## Part I: My Network Topology Overview (10-15 minutes)

### My Introduction (1-2 minutes)
**What I'll Say:**
"Hi! I'm Tshepang, and welcome to my NetSimX project demonstration for CMPG 325 Computer Networks. Today I'll be showing you the comprehensive network I've built, featuring five core topologies plus a hybrid integration. Through this project, I've learned practical implementation of networking concepts including IPv4/IPv6 dual-stack, VLANs, network services, and enterprise-level integration."

**What I'll Show on Screen:**
- My project overview 
- My GitHub repository
- My main README.md file

### 1. Bus Topology Demonstration (2 minutes)
**Script:**
"First, let's examine the Bus topology implementation. This linear topology connects five PCs through a central hub, demonstrating shared bandwidth and collision domain concepts."

**Show:**
- [ ] Open bus-topology.pkt
- [ ] Point out linear arrangement of devices
- [ ] Show IP configuration on PC1 (192.168.1.10)
- [ ] Demonstrate ping from PC1 to PC5
- [ ] Show ARP table
- [ ] Explain shared collision domain

**Key Points:**
- IPv4 addressing: 192.168.1.0/24
- Shared bandwidth demonstration
- Single collision domain
- CSMA/CD protocol in action

### 2. Mesh Topology Demonstration (2 minutes)
**Script:**
"The Mesh topology provides redundancy through multiple paths between routers. This implementation uses OSPF routing protocol for dynamic path selection."

**Show:**
- [ ] Open mesh-topology.pkt
- [ ] Show router interconnections
- [ ] Display OSPF neighbor relationships
- [ ] Show routing table on Router1
- [ ] Simulate link failure
- [ ] Show route convergence

**Key Points:**
- Full mesh connectivity
- OSPF routing protocol
- Redundancy and fault tolerance
- Route convergence demonstration

### 3. Star Topology Demonstration (2 minutes)
**Script:**
"The Star topology centers all connectivity through a managed switch, enabling VLAN segmentation and centralized management."

**Show:**
- [ ] Open star-topology.pkt
- [ ] Show central switch configuration
- [ ] Display VLAN configuration
- [ ] Show MAC address table
- [ ] Demonstrate inter-VLAN communication
- [ ] Show switch port status

**Key Points:**
- Central switch management
- VLAN implementation
- Broadcast domain control
- Scalability features

### 4. Ring Topology Demonstration (2 minutes)
**Script:**
"The Ring topology uses Spanning Tree Protocol to prevent loops while maintaining backup paths for redundancy."

**Show:**
- [ ] Open ring-topology.pkt
- [ ] Show circular switch connections
- [ ] Display spanning tree status
- [ ] Show root bridge election
- [ ] Demonstrate path failure recovery
- [ ] Show port roles and states

**Key Points:**
- Spanning Tree Protocol
- Loop prevention
- Root bridge election
- Automatic failover

### 5. Extended Star Demonstration (2 minutes)
**Script:**
"The Extended Star topology demonstrates hierarchical network design with core and access layers, supporting enterprise scalability."

**Show:**
- [ ] Open extended-star-topology.pkt
- [ ] Show hierarchical structure
- [ ] Display trunk configurations
- [ ] Show VLAN propagation
- [ ] Demonstrate inter-VLAN routing
- [ ] Show core switch capabilities

**Key Points:**
- Hierarchical design
- Core/Access layer model
- VLAN trunking
- Scalable architecture

### 6. Hybrid Integration Overview (3-4 minutes)
**Script:**
"The Hybrid topology integrates all previous topologies into a comprehensive enterprise network, demonstrating real-world network design principles."

**Show:**
- [ ] Open hybrid-integration.pkt
- [ ] Show overall network diagram
- [ ] Demonstrate inter-topology communication
- [ ] Show routing between different segments
- [ ] Display VLAN isolation
- [ ] Show security implementations
- [ ] Test end-to-end connectivity

**Key Points:**
- Multi-topology integration
- Enterprise design principles
- Complex routing scenarios
- Security segmentation

---

## Part II: Network Services Demonstration (5-15 minutes)

### Introduction to Services (1 minute)
**Script:**
"Now let's examine the network services that provide essential functionality across our integrated network infrastructure."

### 1. Email Server Demonstration (3-4 minutes)
**Script:**
"The email server provides SMTP, POP3, and IMAP services for network-wide email communication."

**Show:**
- [ ] Open email server configuration
- [ ] Show server IP: 192.168.100.10
- [ ] Display user accounts
- [ ] Configure email client on PC
- [ ] Send test email between users
- [ ] Show email delivery
- [ ] Check server logs

**Demonstrate:**
- Email account creation
- Client configuration
- Send/receive functionality
- Multiple user testing

### 2. Web Server Demonstration (2 minutes)
**Script:**
"The web server hosts websites accessible from all network segments, demonstrating HTTP service integration."

**Show:**
- [ ] Open web server configuration
- [ ] Show server IP: 192.168.100.20
- [ ] Access website from different VLANs
- [ ] Show web content
- [ ] Demonstrate virtual hosts
- [ ] Test from multiple clients

**Demonstrate:**
- Web page access
- Cross-VLAN connectivity
- Service availability

### 3. DNS Service Demonstration (2 minutes)
**Script:**
"DNS service provides name resolution, enabling users to access services by hostname rather than IP address."

**Show:**
- [ ] Open DNS server configuration
- [ ] Show zone configurations
- [ ] Demonstrate name resolution
- [ ] Test from command line
- [ ] Show A records
- [ ] Test MX records

**Commands to show:**
```bash
nslookup mail.netsimx.local
nslookup web.netsimx.local
nslookup -type=mx netsimx.local
```

### 4. DHCP Service Demonstration (2 minutes)
**Script:**
"DHCP service provides automatic IP configuration for client devices across all network segments."

**Show:**
- [ ] Open DHCP server configuration
- [ ] Show pool configurations
- [ ] Demonstrate automatic IP assignment
- [ ] Show lease table
- [ ] Test from new client
- [ ] Show pool statistics

**Demonstrate:**
- Automatic IP assignment
- Multiple pool management
- Lease monitoring

### Integration Testing (2-3 minutes)
**Script:**
"Finally, let's demonstrate the complete integration with end-to-end testing across all topologies and services."

**Show:**
- [ ] PC from Bus topology accessing web server
- [ ] Email communication between different VLANs
- [ ] DNS resolution from all segments
- [ ] DHCP assignment in different topologies
- [ ] Security isolation verification
- [ ] Performance monitoring

---

## Closing Summary (1-2 minutes)
**Script:**
"This NetSimX project demonstrates comprehensive networking knowledge including:
- Five distinct topology implementations
- Hybrid integration design
- Enterprise network services
- IPv4/IPv6 dual-stack implementation
- VLAN segmentation and security
- Real-world application scenarios

The project showcases practical skills in network design, implementation, testing, and documentation. All source files, configurations, and documentation are available in the GitHub repository for detailed review."

**Show:**
- [ ] GitHub repository overview
- [ ] Documentation summary
- [ ] Final network diagram
- [ ] Project statistics

---

## Post-Recording Checklist
- [ ] Video quality review
- [ ] Audio quality check
- [ ] Content completeness verification
- [ ] Duration within requirements (15-30 minutes)
- [ ] Upload to appropriate platform
- [ ] Generate shareable link
- [ ] Test link accessibility
- [ ] Add to project documentation

---

## Technical Requirements

### Recording Setup
- **Resolution**: 1080p minimum
- **Frame Rate**: 30fps
- **Audio**: Clear narration throughout
- **Software**: OBS Studio, Camtasia, or similar

### Screen Recording Tips
- Use full screen for Packet Tracer
- Zoom in for detailed configurations
- Use cursor highlighting
- Pause for transitions
- Keep consistent pacing

### Audio Tips
- Test microphone before recording
- Minimize background noise
- Speak clearly and at moderate pace
- Practice script beforehand
- Leave brief pauses for editing

---

## File Deliverables
- `netsimx-demo-video.mp4` - Complete demonstration video
- `demo-script.md` - This script file
- `demo-slides.pptx` - Introduction/summary slides
- `demo-checklist.md` - Pre/post recording checklist

---

*This demonstration script ensures comprehensive coverage of all project requirements while maintaining professional presentation standards for academic assessment.*
