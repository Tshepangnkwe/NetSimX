# NetSimX - Computer Networks Individual Project

**CMPG 325 - Computer Networks Individual Semester-Long Project 2025**  
**Student**: Tshepang Nkwe  
**Institution**: North-West University, Faculty of Natural & Agricultural Science  
**Department**: Computer Science  
**Submission Date**: October 13, 2025

## 📋 Project Overview

This project demonstrates the design, configuration, and simulation of multiple network topologies using Cisco Packet Tracer, including network services implementation and comprehensive documentation.

### Project Components
1. **Part I**: Network Topologies Design & Simulation (60%)
2. **Part II**: Individual Network Feature Configuration - Email Server (20%)
3. **Part III**: Documentation and GitHub Integration (20%)

## 🌐 Network Topologies Implemented

### 1. Bus Topology
- **File**: `bus-topology.pkt`
- **Description**: Linear network design with shared communication medium
- **Devices**: Hub, 4 PCs
- **IP Range**: 192.168.1.0/24
- **Testing**: Successful ping communication between all devices

### 2. Star Topology  
- **File**: `star-topology.pkt`
- **Description**: Centralized network with switch as central connection point
- **Devices**: Switch (2960), 4 PCs, 1 Server (HTTP)
- **IP Range**: 192.168.2.0/24
- **Testing**: Full connectivity and HTTP server access verified

### 3. Ring Topology
- **File**: `ring-topology.pkt`
- **Description**: Circular network configuration with token passing simulation
- **Devices**: 4 PCs connected in ring formation using switches
- **IP Range**: 192.168.3.0/24
- **Testing**: Circular connectivity confirmed

### 4. Mesh Topology
- **File**: `mesh-topology.pkt`
- **Description**: Full mesh connectivity for redundancy and reliability
- **Devices**: 4 Routers in full mesh configuration
- **IP Range**: Multiple subnets (10.0.x.0/30 for links)
- **Testing**: Multiple path connectivity and failover capability

### 5. Extended Star Topology
- **File**: `extended-star-topology.pkt`
- **Description**: Hierarchical network design with core and access layers
- **Devices**: Core switch, 2 access switches, 6 PCs
- **IP Range**: 192.168.5.0/24
- **Testing**: Inter-switch communication and scalability demonstration

### 6. Hybrid Topology
- **File**: `hybrid-topology.pkt`
- **Description**: Integration of multiple topology elements with advanced features
- **Features**: 
  - IPv4 and IPv6 dual-stack configuration
  - VLAN segmentation (Sales: VLAN 10, HR: VLAN 20, IT: VLAN 30)
  - Inter-VLAN routing
  - Network services integration
- **Security**: Basic ACLs and password protection implemented

## 🔧 Network Services Implementation

### Email Server Configuration
- **File**: `email-server.pkt`
- **Services Implemented**:
  - SMTP (Simple Mail Transfer Protocol) - Port 25
  - POP3 (Post Office Protocol) - Port 110
  - IMAP (Internet Message Access Protocol) - Port 143
  - HTTP (Web Mail Interface) - Port 80
  - DNS (Domain Name System) for mail routing

### Server Details
- **Email Server IP**: 192.168.1.10
- **DNS Server IP**: 192.168.1.20
- **Domain**: company.com
- **User Accounts**: 3 configured users with different access methods
- **Testing**: Email sending, receiving, and multiple protocol access verified

## 📊 IP Addressing Plan

| Topology | Network | Subnet Mask | Gateway | DHCP Range |
|----------|---------|-------------|---------|------------|
| Bus | 192.168.1.0/24 | 255.255.255.0 | N/A | Static IPs |
| Star | 192.168.2.0/24 | 255.255.255.0 | 192.168.2.1 | .10-.50 |
| Ring | 192.168.3.0/24 | 255.255.255.0 | N/A | Static IPs |
| Mesh | 10.0.x.0/30 | 255.255.255.252 | Various | Point-to-point |
| Extended Star | 192.168.5.0/24 | 255.255.255.0 | 192.168.5.1 | .100-.200 |
| Hybrid | Multiple VLANs | 255.255.255.0 | Per VLAN | Per VLAN |
| Email System | 192.168.1.0/24 | 255.255.255.0 | 192.168.1.1 | .100-.150 |

## 🔐 Security Implementation

### Basic Security Features
- **Password Protection**: Enabled on all network devices
- **Access Control Lists (ACLs)**: Implemented on routers and switches
- **VLAN Segmentation**: Logical separation of network traffic
- **Port Security**: MAC address limiting on switch ports
- **Service Hardening**: Unnecessary services disabled

### Security Testing
- Authentication mechanisms tested and verified
- Access control policies enforced
- Network segmentation validated

## ✅ Testing and Validation

### Connectivity Testing
- **Ping Tests**: Successful communication verified between all devices
- **Service Access**: HTTP, DNS, and email services tested and operational
- **Protocol Verification**: Multiple email protocols (SMTP, POP3, IMAP) confirmed working
- **VLAN Communication**: Inter-VLAN routing successfully implemented

### Performance Metrics
- All topologies demonstrate expected behavior patterns
- Network services respond within acceptable timeframes
- Security policies enforce intended access restrictions
- Scalability demonstrated through extended star design

## 📁 File Structure

```
NetSimX/
├── topologies/
│   ├── bus-topology.pkt
│   ├── star-topology.pkt
│   ├── ring-topology.pkt
│   ├── mesh-topology.pkt
│   ├── extended-star-topology.pkt
│   ├── hybrid-topology.pkt
│   └── email-server.pkt
├── docs/
│   ├── configuration-notes.md
│   ├── testing-results.md
│   └── ip-addressing-plan.csv
└── README.md (this file)
```

## 🛠️ Tools and Technologies

- **Primary Tool**: Cisco Packet Tracer 8.2.1
- **Operating System**: Windows 11
- **Documentation**: Markdown, Git version control
- **Repository**: GitHub (https://github.com/Tshepangnkwe/NetSimX)

## 📈 Learning Outcomes Achieved

### Technical Skills Demonstrated
- Network topology design and implementation
- Cisco device configuration (routers, switches, servers)
- IP addressing and subnetting
- Network services configuration
- Basic security implementation
- Network troubleshooting and testing

### Professional Skills Applied
- Project planning and time management
- Technical documentation
- Version control with Git
- Problem-solving and critical thinking

## 🎯 Project Deliverables Summary

✅ **Network Topologies**: 6 complete .pkt files with working configurations  
✅ **Email Server**: Fully functional with multiple protocol support  
✅ **Documentation**: Comprehensive README and technical notes  
✅ **IP Addressing**: Complete addressing scheme with planning table  
✅ **Security Implementation**: Basic ACLs and access controls  
✅ **GitHub Integration**: Version controlled with proper commit history  
✅ **Testing Validation**: All components tested and verified functional  

## 📋 Submission Checklist

- [x] All .pkt files created and tested
- [x] Email server implementation completed
- [x] Documentation uploaded to GitHub
- [x] IP addressing plan documented
- [x] Security features implemented
- [x] README.md file completed
- [x] Project submitted before deadline (Oct 13, 2025 @ 23:55)

---

**Total Project Completion**: 100%  
**Expected Grade**: Pass (60+ marks achieved through implementation and documentation)

**Note**: This project demonstrates practical understanding of computer networking concepts through hands-on simulation and implementation using industry-standard tools.