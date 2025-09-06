# ⭐ My Star Topology Implementation

## What I'm Building
For this part of my CMPG 325 project, I'm creating a star topology with all my devices connecting to one central switch. This is what most networks look like in real life!

## My Network Design

### How I'm Setting Up My Star Topology
- **Architecture**: One central switch with all my devices connecting to it like spokes on a wheel
- **Central Device**: A managed switch that I'll configure myself
- **End Devices**: 6-8 PCs and 1 server that I'll connect
- **Cable Type**: Cat5e straight-through cables for all connections

### My IP Address Plan

#### IPv4 Configuration I'm Using
- **Network**: 192.168.3.0/24
- **Subnet Mask**: 255.255.255.0
- **Gateway**: 192.168.3.1 (This is how I'll manage my switch)

| Device | Hostname | IPv4 Address | Subnet Mask | Switch Port | MAC Address |
|--------|----------|--------------|-------------|-------------|-------------|
| Switch1 | STAR-SW01 | 192.168.3.1 | 255.255.255.0 | Management | Auto |
| PC1 | STAR-PC01 | 192.168.3.10 | 255.255.255.0 | Fa0/1 | Auto |
| PC2 | STAR-PC02 | 192.168.3.11 | 255.255.255.0 | Fa0/2 | Auto |
| PC3 | STAR-PC03 | 192.168.3.12 | 255.255.255.0 | Fa0/3 | Auto |
| PC4 | STAR-PC04 | 192.168.3.13 | 255.255.255.0 | Fa0/4 | Auto |
| PC5 | STAR-PC05 | 192.168.3.14 | 255.255.255.0 | Fa0/5 | Auto |
| PC6 | STAR-PC06 | 192.168.3.15 | 255.255.255.0 | Fa0/6 | Auto |
| Server1 | STAR-SRV01 | 192.168.3.100 | 255.255.255.0 | Fa0/24 | Auto |

#### IPv6 Configuration
- **Network**: 2001:db8:3::/64
- **Link-local**: fe80::/64

| Device | IPv6 Address | Prefix |
|--------|--------------|--------|
| PC1 | 2001:db8:3::10/64 | 64 |
| PC2 | 2001:db8:3::11/64 | 64 |
| PC3 | 2001:db8:3::12/64 | 64 |
| PC4 | 2001:db8:3::13/64 | 64 |
| PC5 | 2001:db8:3::14/64 | 64 |
| PC6 | 2001:db8:3::15/64 | 64 |
| Server1 | 2001:db8:3::100/64 | 64 |

## Implementation Steps

### 1. Physical Layout
1. Place central switch (2960-24TT) in center
2. Arrange PCs in star pattern around switch
3. Connect each device to switch with straight-through cables
4. Place server on dedicated port (Fa0/24)

### 2. Switch Configuration

#### Basic Switch Setup
```cisco
Switch> enable
Switch# configure terminal
Switch(config)# hostname STAR-SW01
Switch(config)# interface vlan1
Switch(config-if)# ip address 192.168.3.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit
Switch(config)# ip default-gateway 192.168.3.1
```

#### Port Configuration
```cisco
Switch(config)# interface range FastEthernet0/1-6
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 1
Switch(config-if-range)# no shutdown
Switch(config-if-range)# exit
```

#### Port Security (Optional)
```cisco
Switch(config)# interface FastEthernet0/1
Switch(config-if)# switchport port-security
Switch(config-if)# switchport port-security maximum 1
Switch(config-if)# switchport port-security violation restrict
```

### 3. VLAN Configuration

#### Creating VLANs
```cisco
Switch(config)# vlan 10
Switch(config-vlan)# name Users
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# name Servers
Switch(config-vlan)# exit
```

#### Assigning Ports to VLANs
```cisco
Switch(config)# interface range FastEthernet0/1-6
Switch(config-if-range)# switchport access vlan 10
Switch(config-if-range)# exit
Switch(config)# interface FastEthernet0/24
Switch(config-if)# switchport access vlan 20
```

## Testing Procedures

### Connectivity Testing
- Ping tests between all PCs
- Server accessibility from all PCs
- Switch management interface testing
- VLAN isolation verification

### Performance Analysis
- Bandwidth testing
- Latency measurements
- Switch MAC address table analysis
- Port utilization monitoring

### Security Testing
- Port security functionality
- VLAN separation verification
- Broadcast domain analysis

## Key Features

### Advantages
- **Centralized Management**: Easy to configure and manage
- **Scalability**: Easy to add/remove devices
- **Performance**: Each device gets full bandwidth
- **Fault Isolation**: Problems isolated to individual connections
- **Security**: VLANs provide traffic separation

### Disadvantages
- **Single Point of Failure**: Central switch failure affects all devices
- **Cable Requirements**: More cables needed than bus topology
- **Cost**: Requires active switching equipment
- **Distance Limitations**: Limited by cable length specifications

## Documentation Requirements

### Switch Information to Collect
- MAC address table entries
- Port status and utilization
- VLAN configuration
- Spanning tree protocol status
- Port security settings

### Testing Documentation
- Connectivity test results
- Performance measurements
- Security verification
- VLAN functionality tests

## Files in this Directory
- `star-topology.pkt` - Cisco Packet Tracer file
- `config-backup/` - Switch and device configurations
- `screenshots/` - Implementation screenshots
- `testing-results.md` - Connectivity and performance tests
- `vlan-config.md` - VLAN implementation details

---
*Part of NetSimX - CMPG 325 Computer Networks Project*
