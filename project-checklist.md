# NetSimX Project Checklist

## CMPG 325 Computer Networks - Project Progress Tracker

### Project Overview
- **Total Marks**: 100
- **Submission Deadline**: 13-October-2025 @23:55
- **Current Status**: In Progress ⏳

---

## Part I - Network Topologies Design & Simulation (70 marks)

### 🌐 Core Topologies Implementation

#### 1. Bus Topology (12 marks)
- [ ] Create Packet Tracer file (.pkt)
- [ ] Configure 5-6 devices in linear bus arrangement
- [ ] Set up IPv4 addressing (192.168.1.0/24)
- [ ] Configure IPv6 addressing (2001:db8:1:1::/64)
- [ ] Test connectivity between all devices
- [ ] Document configuration in README.md
- [ ] Capture screenshots (topology, configs, ping tests)
- [ ] Export device configurations

**Key Requirements:**
- Linear bus topology with proper termination
- All devices on same collision domain
- Shared bandwidth demonstration
- CSMA/CD implementation evidence

#### 2. Mesh Topology (12 marks)
- [ ] Create full or partial mesh design
- [ ] Implement redundant paths between routers
- [ ] Configure routing protocols (OSPF/RIP)
- [ ] Set up IPv4/IPv6 dual-stack
- [ ] Test path redundancy (link failure simulation)
- [ ] Document routing tables
- [ ] Create network diagram
- [ ] Performance testing documentation

**Key Requirements:**
- Multiple paths between nodes
- Fault tolerance demonstration
- Routing protocol configuration
- Path selection verification

#### 3. Star Topology (12 marks)
- [ ] Central switch/hub configuration
- [ ] Connect 6-8 end devices to central point
- [ ] Configure switch ports and VLANs
- [ ] Set up IPv4/IPv6 addressing
- [ ] Test broadcast domain behavior
- [ ] Document switch configuration
- [ ] MAC address table analysis
- [ ] Port security implementation

**Key Requirements:**
- Central point of connectivity
- All traffic through central device
- Single point of failure demonstration
- Easy scalability evidence

#### 4. Ring Topology (12 marks)
- [ ] Create logical ring using switches
- [ ] Configure token passing (if available)
- [ ] Set up redundant ring paths
- [ ] Implement spanning tree protocol
- [ ] Test ring failure recovery
- [ ] Document ring operation
- [ ] Performance metrics collection
- [ ] Troubleshooting procedures

**Key Requirements:**
- Circular data flow pattern
- Token-based access (conceptual)
- Ring break recovery
- Equal access demonstration

#### 5. Extended Star Topology (12 marks)
- [ ] Core switch configuration
- [ ] Multiple access layer switches
- [ ] Hierarchical design implementation
- [ ] VLAN configuration across switches
- [ ] Inter-VLAN routing setup
- [ ] Spanning tree configuration
- [ ] Load balancing implementation
- [ ] Scalability demonstration

**Key Requirements:**
- Hierarchical structure (Core/Access)
- Multiple stars connected
- VLAN segmentation
- Centralized management

#### 6. Hybrid Integration (10 marks)
- [ ] Combine elements from all topologies
- [ ] Router interconnections between topologies
- [ ] IPv4/IPv6 routing between networks
- [ ] VLAN trunking configuration
- [ ] Inter-topology communication testing
- [ ] Security implementation (ACLs)
- [ ] Performance optimization
- [ ] Complete network documentation

**Key Requirements:**
- Integration of multiple topology types
- Seamless communication between networks
- Creative design implementation
- Security and performance considerations

---

## Network Services Configuration

### 🌐 Core Network Services (Integrated into topologies)

#### HTTP/Web Server
- [ ] Configure web server in server farm
- [ ] Create basic web pages
- [ ] Test HTTP connectivity from clients
- [ ] Configure virtual hosts (if available)
- [ ] Document web server configuration
- [ ] Performance testing

#### DNS Server
- [ ] Set up primary DNS server
- [ ] Configure forward lookup zones
- [ ] Create A, CNAME, MX records
- [ ] Configure reverse lookup zones
- [ ] Test DNS resolution from clients
- [ ] Document DNS configuration

#### DHCP Server
- [ ] Configure DHCP pools for each network
- [ ] Set up scope options (gateway, DNS)
- [ ] Configure DHCP reservations
- [ ] Test automatic IP assignment
- [ ] Monitor DHCP lease table
- [ ] Document DHCP configuration

### 🔒 Security Implementation
- [ ] VLAN segmentation across networks
- [ ] Access Control Lists (ACLs)
- [ ] Port security on switches
- [ ] Basic firewall rules
- [ ] Network monitoring setup
- [ ] Security testing and validation

---

## Part II - Email Server Configuration (30 marks)

### 📧 Email Server Implementation

#### Server Setup
- [ ] Deploy Server-PT device
- [ ] Configure static IP addressing
- [ ] Enable SMTP service
- [ ] Configure POP3/IMAP (if available)
- [ ] Set up email domain (netsimx.local)
- [ ] Configure DNS MX records

#### User Management
- [ ] Create email user accounts
  - [ ] admin@netsimx.local
  - [ ] user1@netsimx.local
  - [ ] user2@netsimx.local
  - [ ] test@netsimx.local
- [ ] Set up authentication
- [ ] Configure mailbox storage
- [ ] Test user login

#### Client Configuration
- [ ] Configure email clients on workstations
- [ ] Set up incoming mail settings (POP3/IMAP)
- [ ] Configure outgoing mail settings (SMTP)
- [ ] Test email client connectivity
- [ ] Verify authentication

#### Testing & Validation
- [ ] Send emails between local users
- [ ] Test email delivery and receipt
- [ ] Verify email storage on server
- [ ] Test multiple simultaneous users
- [ ] Document all test results
- [ ] Troubleshoot any issues

#### Documentation
- [ ] Complete server configuration guide
- [ ] Client setup instructions
- [ ] Troubleshooting procedures
- [ ] Performance metrics
- [ ] Security considerations

---

## Part III - Video Demonstration (No separate marks, integrated into above)

### 🎬 Video Planning (15-30 minutes)

#### Part 1: Topology Overview (10-15 minutes)
- [ ] Script preparation
- [ ] Network topology walkthrough
- [ ] Configuration highlights
- [ ] Connectivity demonstrations
- [ ] Protocol explanations
- [ ] Hybrid integration showcase

#### Part 2: Services & Email Demo (5-15 minutes)
- [ ] Email server demonstration
- [ ] Send/receive email testing
- [ ] Web server functionality
- [ ] DNS resolution testing
- [ ] DHCP operation demonstration
- [ ] Security features explanation

#### Production Requirements
- [ ] Screen recording software setup
- [ ] Audio quality testing
- [ ] Practice run and timing
- [ ] Final recording
- [ ] Video editing (if needed)
- [ ] Upload and submission preparation

---

## Documentation Requirements

### 📚 GitHub Documentation

#### Repository Structure
- [ ] README.md (project overview)
- [ ] project-requirements.md
- [ ] Individual topology READMEs
- [ ] IP addressing documentation
- [ ] Configuration backup files
- [ ] Screenshots collection
- [ ] Video demonstration link

#### Technical Documentation
- [ ] Complete IP addressing tables
- [ ] Device configuration exports
- [ ] Network diagrams
- [ ] Testing procedures and results
- [ ] Troubleshooting guides
- [ ] Performance analysis

#### Git Management
- [ ] Regular commits with meaningful messages
- [ ] Branching strategy (if applicable)
- [ ] Tag releases for major milestones
- [ ] Clean repository structure
- [ ] Proper .gitignore configuration

---

## Quality Assurance Checklist

### 🔍 Pre-Submission Validation

#### Technical Validation
- [ ] All .pkt files open correctly in Packet Tracer
- [ ] Network connectivity tests pass
- [ ] All services function as expected
- [ ] Configuration backups are complete
- [ ] Documentation is accurate and complete

#### Documentation Review
- [ ] All README files are comprehensive
- [ ] Screenshots are clear and relevant
- [ ] IP addressing tables are accurate
- [ ] Configuration notes are detailed
- [ ] Video demonstrates all requirements

#### Final Submission
- [ ] Repository is organized and clean
- [ ] All files are properly committed
- [ ] Video is uploaded and accessible
- [ ] Submission meets deadline requirements
- [ ] Backup copies created

---

## Grading Rubric Reference

### Network Topologies Design & Simulation (70 marks)
| Criteria | Excellent (15) | Good (12) | Fair (9) | Poor (6) |
|----------|----------------|-----------|----------|----------|
| **Topology Design Accuracy** | Perfect implementation matching theoretical concepts | Minor deviations from standard design | Some design issues present | Major design flaws |
| **Device Configuration** | All devices properly configured with optimal settings | Most devices configured correctly | Basic configuration present | Poor or incomplete configuration |
| **Data Exchange Evidence** | Comprehensive testing with detailed results | Good testing with clear results | Basic testing performed | Limited or unclear testing |
| **Hybrid Creativity** | Innovative integration showing deep understanding | Good integration with some creativity | Basic integration attempt | Poor or no integration |
| **IP Addressing Plan** | Complete, logical, and well-documented plan | Good plan with minor issues | Basic plan present | Incomplete or poor planning |
| **Documentation** | Excellent documentation with all requirements | Good documentation with most requirements | Basic documentation present | Poor or incomplete documentation |

### Individual Network Feature (30 marks)
| Criteria | Excellent (15) | Good (12) | Fair (9) | Poor (6) |
|----------|----------------|-----------|----------|----------|
| **Configuration & Functionality** | Perfect email server setup with all features working | Good setup with minor issues | Basic functionality present | Poor or non-functional setup |
| **Documentation** | Complete and detailed documentation | Good documentation present | Basic documentation | Poor or missing documentation |

---

## Timeline & Milestones

### Week 1-2: Foundation (Current)
- [x] Project setup and planning
- [x] Repository initialization
- [ ] Bus topology implementation
- [ ] Documentation framework

### Week 3-4: Core Topologies
- [ ] Mesh topology implementation
- [ ] Star topology implementation
- [ ] Ring topology implementation
- [ ] Extended star implementation

### Week 5-6: Integration & Services
- [ ] Hybrid topology design
- [ ] Network services implementation
- [ ] Email server configuration
- [ ] Security implementation

### Week 7-8: Documentation & Testing
- [ ] Complete documentation
- [ ] Comprehensive testing
- [ ] Video preparation and recording
- [ ] Final quality assurance

### Week 9: Submission
- [ ] Final repository cleanup
- [ ] Video upload
- [ ] Submission preparation
- [ ] Deadline compliance

---

## Notes & Reminders

### Important Dates
- **Project Start**: Current Date
- **Milestone Check**: Weekly
- **Final Submission**: 13-October-2025 @23:55

### Key Success Factors
1. **Regular Progress**: Work consistently, don't leave everything to the last minute
2. **Documentation**: Document as you go, not at the end
3. **Testing**: Test thoroughly after each implementation
4. **Backup**: Regular commits and backups
5. **Quality**: Focus on quality over quantity

### Support Resources
- **Cisco Packet Tracer Documentation**
- **Course Materials and Textbooks**
- **Online Cisco Learning Resources**
- **University Support Services**

---

*This checklist will be updated as the project progresses. Check off items as they are completed and add notes as needed.*

**Current Progress**: Initial Setup Complete ✅
**Next Priority**: Bus Topology Implementation 🎯
