# Bus Topology Implementation

## Overview
Bus topology is a network architecture where all devices are connected to a single shared communication line (backbone cable). This implementation demonstrates fundamental networking concepts with modern protocols.

## Network Design

### Topology Characteristics
- **Architecture**: Linear bus with terminator resistors
- **Cable Type**: Ethernet backbone (simulated coaxial in Packet Tracer)
- **Devices**: 5-8 computers/workstations
- **Termination**: Proper termination at both ends

### IP Addressing Scheme

#### IPv4 Configuration
- **Network**: 192.168.1.0/24
- **Subnet Mask**: 255.255.255.0
- **Gateway**: 192.168.1.1

| Device | IPv4 Address | Subnet Mask | Gateway |
|--------|--------------|-------------|---------|
| PC1 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| PC3 | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 |
| PC4 | 192.168.1.13 | 255.255.255.0 | 192.168.1.1 |
| PC5 | 192.168.1.14 | 255.255.255.0 | 192.168.1.1 |

#### IPv6 Configuration
- **Network**: 2001:db8:1::/64
- **Link-local**: fe80::/64

| Device | IPv6 Address | Prefix |
|--------|--------------|--------|
| PC1 | 2001:db8:1::10/64 | 64 |
| PC2 | 2001:db8:1::11/64 | 64 |
| PC3 | 2001:db8:1::12/64 | 64 |
| PC4 | 2001:db8:1::13/64 | 64 |
| PC5 | 2001:db8:1::14/64 | 64 |

## Implementation Steps

### 1. Physical Layout
1. Open Cisco Packet Tracer
2. Place 5-6 generic PCs in a linear arrangement
3. Connect using straight-through cables to simulate bus backbone
4. Add hub/repeater if needed for signal amplification

### 2. Device Configuration

#### PC Configuration Commands
```bash
# IPv4 Configuration
ipconfig /ip 192.168.1.10 255.255.255.0 192.168.1.1

# IPv6 Configuration  
ipv6config /ipv6 2001:db8:1::10/64
```

### 3. Testing & Validation

#### Connectivity Tests
- **Ping Test**: Verify end-to-end connectivity
- **Traceroute**: Confirm routing path
- **ARP Table**: Check MAC address resolution

#### Test Commands
```bash
# IPv4 Connectivity
ping 192.168.1.11
ping 192.168.1.14

# IPv6 Connectivity  
ping 2001:db8:1::11
ping 2001:db8:1::14

# Network Discovery
arp -a
ipconfig /all
```

## Advantages & Disadvantages

### Advantages
- **Simple Installation**: Easy to set up and configure
- **Cost-Effective**: Minimal cable requirements
- **Easy Troubleshooting**: Linear structure simplifies fault isolation

### Disadvantages
- **Single Point of Failure**: Backbone failure affects entire network
- **Performance Degradation**: Bandwidth shared among all devices
- **Limited Scalability**: Performance decreases as devices increase
- **Collision Domain**: All devices share same collision domain

## Configuration Notes

### Key Considerations
1. **Termination**: Ensure proper termination to prevent signal reflection
2. **Cable Length**: Monitor total cable length for signal integrity
3. **Collision Detection**: Implement CSMA/CD for collision management
4. **Bandwidth Sharing**: Understand shared bandwidth implications

### Security Implementation
- **Basic ACLs**: Implement access control lists
- **Port Security**: Configure port-based security
- **VLAN Segmentation**: Create VLANs for traffic isolation

## Files in this Directory
- `bus-topology.pkt` - Cisco Packet Tracer file
- `config-backup/` - Device configuration backups
- `screenshots/` - Implementation screenshots
- `testing-results.md` - Connectivity test results

## Screenshots Required
1. Network topology overview
2. IP configuration on each device
3. Successful ping tests (IPv4 & IPv6)
4. ARP table entries
5. Network performance metrics

## Next Steps
After completing this topology:
1. Document all configurations
2. Capture required screenshots
3. Test all connectivity scenarios
4. Prepare for hybrid integration
5. Update main project documentation

---
*Part of NetSimX - CMPG 325 Computer Networks Project*
