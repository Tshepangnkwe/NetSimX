# Configuration Notes - NetSimX Project

## Device Configuration Summary

### Bus Topology Configuration
**File**: `bus-topology.pkt`
- **Hub Configuration**: Default settings, no IP required
- **PC IP Addresses**:
  - PC1: 192.168.1.10/24
  - PC2: 192.168.1.11/24
  - PC3: 192.168.1.12/24
  - PC4: 192.168.1.13/24

### Star Topology Configuration
**File**: `star-topology.pkt`
- **Switch Configuration**: Default VLAN, no management IP
- **PC IP Addresses**:
  - PC1: 192.168.2.10/24
  - PC2: 192.168.2.11/24
  - PC3: 192.168.2.12/24
  - PC4: 192.168.2.13/24
- **Server Configuration**:
  - Web Server: 192.168.2.20/24
  - HTTP Service: Enabled on port 80

### Ring Topology Configuration
**File**: `ring-topology.pkt`
- **Switch Configuration**: Multiple switches connected in ring
- **PC IP Addresses**:
  - PC1: 192.168.3.10/24
  - PC2: 192.168.3.11/24
  - PC3: 192.168.3.12/24
  - PC4: 192.168.3.13/24

### Mesh Topology Configuration
**File**: `mesh-topology.pkt`
- **Router Configuration**:
  - R1: Serial interfaces with point-to-point IPs
  - R2: Serial interfaces with point-to-point IPs
  - R3: Serial interfaces with point-to-point IPs
  - R4: Serial interfaces with point-to-point IPs
- **Routing Protocol**: Static routes or RIP configured

### Extended Star Topology Configuration
**File**: `extended-star-topology.pkt`
- **Core Switch**: Central connectivity point
- **Access Switches**: Connected to core switch
- **PC Distribution**: 2-3 PCs per access switch
- **IP Addressing**: 192.168.5.0/24 network

### Hybrid Topology Configuration
**File**: `hybrid-topology.pkt`
- **VLAN Configuration**:
  - VLAN 10 (Sales): 192.168.10.0/24
  - VLAN 20 (HR): 192.168.20.0/24
  - VLAN 30 (IT): 192.168.30.0/24
- **Inter-VLAN Routing**: Configured on Layer 3 switch or router
- **Services**: DNS, DHCP, HTTP servers implemented

### Email Server Configuration
**File**: `email-server.pkt`
- **Email Server IP**: 192.168.1.10/24
- **DNS Server IP**: 192.168.1.20/24
- **Services Enabled**:
  - SMTP: Port 25
  - POP3: Port 110
  - IMAP: Port 143
  - HTTP: Port 80
- **User Accounts**:
  - john.doe@company.com
  - jane.smith@company.com
  - admin@company.com

## Security Configuration

### Password Protection
- All routers and switches configured with enable secret passwords
- Console and VTY line passwords set
- Password encryption enabled

### Access Control Lists (ACLs)
- Basic ACLs implemented to control traffic flow
- Deny unnecessary protocols
- Permit required communication paths

### VLAN Security
- Inter-VLAN communication controlled
- Port security implemented on access ports
- Unused ports disabled

## Testing Procedures

### Connectivity Testing
1. **Ping Tests**: Verify reachability between all devices
2. **Traceroute**: Confirm routing paths in mesh topology
3. **Service Access**: Test HTTP, DNS, and email services
4. **Protocol Verification**: Confirm SMTP, POP3, IMAP functionality

### Common Commands Used
```
ping [destination_ip]
ipconfig
tracert [destination_ip]
nslookup [hostname]
```

## Troubleshooting Notes

### Common Issues Resolved
1. **IP Conflicts**: Ensured unique IP addresses within each subnet
2. **Cable Types**: Used correct cable types for device connections
3. **Service Configuration**: Verified all required services are enabled
4. **Routing Issues**: Configured proper routing in multi-subnet environments

### Validation Steps
1. Check physical connections (green lights)
2. Verify IP configuration on all devices
3. Confirm service status on servers
4. Test end-to-end connectivity
5. Validate security policy enforcement

---

**Note**: All configurations have been tested and validated for proper operation. Screenshots and detailed testing results are available upon request.