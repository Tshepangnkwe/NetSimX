# 🌐 My Mesh Topology Implementation

## What I'm Building
For this part of my CMPG 325 project, I'm creating a mesh topology that shows how networks can have multiple paths between devices. This gives me hands-on experience with redundancy and fault tolerance concepts.

## My Network Design

### What Makes This a Mesh Topology
- **Architecture**: I'm building a full mesh with redundant connections between devices
- **Routing Protocol**: Using OSPF so the routers can automatically find the best paths
- **Devices**: 4 routers that I'll interconnect with multiple paths
- **Redundancy**: If one connection fails, my data can still get through using alternate paths

### How I'm Setting Up the IP Addresses

#### IPv4 Configuration for My Network
- **Main Network**: 192.168.2.0/24
- **Subnet Mask**: 255.255.255.0 
- **Router Connections**: 10.0.0.0/30 networks for the links between routers

| Device | Interface | IPv4 Address | Subnet Mask | Purpose |
|--------|-----------|--------------|-------------|---------|
| Router1 | Fa0/0 | 192.168.2.1 | 255.255.255.0 | LAN Interface |
| Router1 | Fa0/1 | 10.0.0.1 | 255.255.255.252 | To Router2 |
| Router1 | Fa1/0 | 10.0.0.5 | 255.255.255.252 | To Router3 |
| Router2 | Fa0/0 | 192.168.2.2 | 255.255.255.0 | LAN Interface |
| Router2 | Fa0/1 | 10.0.0.2 | 255.255.255.252 | To Router1 |
| Router2 | Fa1/0 | 10.0.0.9 | 255.255.255.252 | To Router4 |
| Router3 | Fa0/0 | 192.168.2.3 | 255.255.255.0 | LAN Interface |
| Router3 | Fa0/1 | 10.0.0.6 | 255.255.255.252 | To Router1 |
| Router3 | Fa1/0 | 10.0.0.13 | 255.255.255.252 | To Router4 |
| Router4 | Fa0/0 | 192.168.2.4 | 255.255.255.0 | LAN Interface |
| Router4 | Fa0/1 | 10.0.0.10 | 255.255.255.252 | To Router2 |
| Router4 | Fa1/0 | 10.0.0.14 | 255.255.255.252 | To Router3 |

#### IPv6 Configuration
- **Network**: 2001:db8:2::/48
- **Subnets**: /64 for each link

| Device | Interface | IPv6 Address | Purpose |
|--------|-----------|--------------|---------|
| Router1 | Fa0/0 | 2001:db8:2:1::1/64 | LAN |
| Router1 | Fa0/1 | 2001:db8:2:12::1/64 | To Router2 |
| Router1 | Fa1/0 | 2001:db8:2:13::1/64 | To Router3 |

## Implementation Steps

### 1. Physical Layout
1. Place 4 routers in mesh configuration
2. Add switches for LAN connectivity
3. Connect PCs to demonstrate end-to-end connectivity
4. Establish redundant paths between routers

### 2. Router Configuration

#### Basic Router Setup
```cisco
Router(config)# hostname MESH-R01
Router(config)# interface FastEthernet0/0
Router(config-if)# ip address 192.168.2.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# ipv6 address 2001:db8:2:1::1/64
Router(config-if)# ipv6 enable
```

#### OSPF Configuration
```cisco
Router(config)# router ospf 1
Router(config-router)# network 192.168.2.0 0.0.0.255 area 0
Router(config-router)# network 10.0.0.0 0.0.0.3 area 0
```

### 3. Testing Procedures

#### Routing Table Verification
- Check OSPF neighbor relationships
- Verify routing table convergence
- Test path redundancy
- Simulate link failures

#### Performance Testing
- Measure convergence times
- Test load balancing
- Verify fault tolerance

## Key Features

### Advantages
- **Redundancy**: Multiple paths prevent single points of failure
- **Load Distribution**: Traffic can be balanced across paths
- **Fast Convergence**: Modern routing protocols ensure quick recovery
- **Scalability**: Easy to add new nodes

### Disadvantages
- **Complexity**: More complex configuration and troubleshooting
- **Cost**: Requires more equipment and cables
- **Routing Overhead**: Protocol traffic for maintaining tables

## Files in this Directory
- `mesh-topology.pkt` - Cisco Packet Tracer file
- `config-backup/` - Router configuration backups
- `screenshots/` - Implementation screenshots
- `testing-results.md` - Routing and connectivity test results

---
*Part of NetSimX - CMPG 325 Computer Networks Project*
