# 🌟 My Extended Star Topology Implementation

## What I'm Building
For this part of my CMPG 325 project, I'm creating an extended star topology that combines multiple star networks through a core switch. This is like building the foundation of a modern enterprise network!

## My Network Design

### How I'm Setting Up the Extended Star
- **Architecture**: I'm building this hierarchically with core and access layers
- **Core Switch**: This is my central aggregation point that connects everything
- **Access Switches**: Each one creates its own individual star network
- **Scalability**: I can easily expand this by adding more access switches later
- **Redundancy**: I might add redundant core connections if I have time

### My IP Address Strategy

#### IPv4 Configuration I'm Using
- **Core Network**: 192.168.5.0/24
- **Access Networks**: I'll subnet 192.168.5.0/26 for each access layer
- **Management VLAN**: 192.168.5.240/28 for managing all my switches

| Device | Hostname | IPv4 Address | Subnet Mask | VLAN | Purpose |
|--------|----------|--------------|-------------|------|---------|
| Core-SW | EXT-CORE-SW | 192.168.5.1 | 255.255.255.0 | 1 | Core Switch |
| Access-SW1 | EXT-ACC-SW1 | 192.168.5.10 | 255.255.255.0 | 1 | Access Layer |
| Access-SW2 | EXT-ACC-SW2 | 192.168.5.11 | 255.255.255.0 | 1 | Access Layer |
| Access-SW3 | EXT-ACC-SW3 | 192.168.5.12 | 255.255.255.0 | 1 | Access Layer |
| PC1-1 | EXT-PC1-1 | 192.168.5.20 | 255.255.255.192 | 10 | User VLAN |
| PC1-2 | EXT-PC1-2 | 192.168.5.21 | 255.255.255.192 | 10 | User VLAN |
| PC2-1 | EXT-PC2-1 | 192.168.5.84 | 255.255.255.192 | 20 | User VLAN |
| PC2-2 | EXT-PC2-2 | 192.168.5.85 | 255.255.255.192 | 20 | User VLAN |
| PC3-1 | EXT-PC3-1 | 192.168.5.148 | 255.255.255.192 | 30 | User VLAN |
| Server1 | EXT-SRV-01 | 192.168.5.200 | 255.255.255.240 | 100 | Server VLAN |

#### IPv6 Configuration
- **Global Prefix**: 2001:db8:5::/48
- **Core Network**: 2001:db8:5:1::/64
- **Access Networks**: 2001:db8:5:10::/64, 2001:db8:5:20::/64, 2001:db8:5:30::/64

### VLAN Design

| VLAN ID | VLAN Name | Network | Purpose | Access Switches |
|---------|-----------|---------|---------|-----------------|
| 1 | Default | 192.168.5.0/24 | Management | All |
| 10 | Users-A | 192.168.5.16/28 | User Group A | SW1 |
| 20 | Users-B | 192.168.5.80/28 | User Group B | SW2 |
| 30 | Users-C | 192.168.5.144/28 | User Group C | SW3 |
| 100 | Servers | 192.168.5.192/28 | Server Network | Core |
| 999 | Management | 192.168.5.240/28 | Network Management | All |

## Implementation Steps

### 1. Physical Layout
1. Place core switch in center (3560 or similar)
2. Place 3 access switches around core
3. Connect access switches to core with trunk links
4. Connect 2 PCs to each access switch
5. Connect server to core switch

### 2. Core Switch Configuration

#### Basic Configuration
```cisco
Switch> enable
Switch# configure terminal
Switch(config)# hostname EXT-CORE-SW
Switch(config)# interface vlan1
Switch(config-if)# ip address 192.168.5.1 255.255.255.0
Switch(config-if)# no shutdown
```

#### VLAN Creation
```cisco
Switch(config)# vlan 10
Switch(config-vlan)# name Users-A
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# name Users-B
Switch(config-vlan)# exit
Switch(config)# vlan 30
Switch(config-vlan)# name Users-C
Switch(config-vlan)# exit
Switch(config)# vlan 100
Switch(config-vlan)# name Servers
Switch(config-vlan)# exit
Switch(config)# vlan 999
Switch(config-vlan)# name Management
```

#### Trunk Configuration
```cisco
Switch(config)# interface range FastEthernet0/1-3
Switch(config-if-range)# switchport mode trunk
Switch(config-if-range)# switchport trunk allowed vlan all
Switch(config-if-range)# no shutdown
```

#### Server Port Configuration
```cisco
Switch(config)# interface FastEthernet0/24
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 100
Switch(config-if)# no shutdown
```

### 3. Access Switch Configuration

#### Access Switch 1 (Users-A)
```cisco
Switch(config)# hostname EXT-ACC-SW1
Switch(config)# vlan 10
Switch(config-vlan)# name Users-A
Switch(config-vlan)# exit

! Trunk to core
Switch(config)# interface FastEthernet0/24
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan 1,10,999

! Access ports
Switch(config)# interface range FastEthernet0/1-2
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 10
```

### 4. Inter-VLAN Routing (if using Layer 3)

#### Core Switch as Layer 3
```cisco
Switch(config)# ip routing
Switch(config)# interface vlan 10
Switch(config-if)# ip address 192.168.5.17 255.255.255.240
Switch(config-if)# no shutdown
Switch(config-if)# exit
Switch(config)# interface vlan 20
Switch(config-if)# ip address 192.168.5.81 255.255.255.240
Switch(config-if)# no shutdown
```

## Testing Procedures

### Hierarchical Connectivity
- Test PC-to-PC within same VLAN
- Test PC-to-PC across VLANs
- Test PC-to-Server connectivity
- Verify trunk link functionality

### VLAN Functionality
- Verify VLAN isolation
- Test inter-VLAN routing
- Validate trunk carrying multiple VLANs
- Check VLAN database consistency

### Scalability Testing
- Add new access switches
- Create additional VLANs
- Test network convergence
- Monitor performance impact

### Fault Tolerance
- Simulate access switch failure
- Test core switch redundancy (if implemented)
- Verify spanning tree operation
- Test rapid recovery times

## Key Features

### Advantages
- **Scalability**: Easy to add new access switches and users
- **Performance**: Dedicated uplinks prevent bottlenecks
- **Management**: Centralized control and monitoring
- **Fault Isolation**: Problems contained to individual access layers
- **VLAN Support**: Traffic segmentation and security
- **Future-Proof**: Supports network growth and changes

### Disadvantages
- **Complexity**: More complex than simple star topology
- **Cost**: Requires multiple switches and management
- **Single Point of Failure**: Core switch is critical
- **Planning Required**: Needs careful VLAN and addressing design

## Design Considerations

### Bandwidth Planning
- Core uplinks: 1Gbps or higher
- Access ports: 100Mbps typical
- Server connections: 1Gbps recommended
- Oversubscription ratios: 20:1 or better

### VLAN Strategy
- Separate user groups by function
- Isolate servers in dedicated VLANs
- Use management VLAN for network devices
- Plan for future VLAN requirements

### Security Implementation
- Port security on access switches
- VLAN ACLs for traffic filtering
- Management VLAN isolation
- Trunk security best practices

## Documentation Requirements

### Network Diagrams
- Physical topology layout
- Logical VLAN structure
- IP addressing scheme
- Trunk link configuration

### Configuration Documentation
- All switch configurations
- VLAN assignments
- Trunk configurations
- IP addressing tables

### Test Results
- Connectivity matrices
- Performance measurements
- VLAN isolation verification
- Scalability test results

## Files in this Directory
- `extended-star-topology.pkt` - Cisco Packet Tracer file
- `config-backup/` - All switch configurations
- `screenshots/` - Network and VLAN screenshots
- `testing-results.md` - Comprehensive test results
- `vlan-design.md` - VLAN implementation details
- `scalability-analysis.md` - Growth and performance analysis

---
*Part of NetSimX - CMPG 325 Computer Networks Project*
