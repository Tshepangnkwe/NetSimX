# 🔄 My Ring Topology Implementation

## What I'm Building Here
For this part of my CMPG 325 project, I'm creating a ring topology where devices connect in a circle. I'll use switches to create this logical ring structure and learn about how data flows in one direction.

## My Network Design

### How I'm Setting Up My Ring
- **Architecture**: I'm creating a circular data path using 4 switches
- **Protocol**: Using Spanning Tree Protocol (STP) to prevent loops from causing problems
- **Devices**: 4 switches connected in a ring plus the end devices I'll connect to them
- **Redundancy**: If my primary path fails, there's a backup path available

### My IP Address Planning

#### IPv4 Configuration for My Ring Network
- **Network**: 192.168.4.0/24
- **Subnet Mask**: 255.255.255.0
- **Management VLAN**: 192.168.4.0/26 (so I can manage my switches)

| Device | Hostname | IPv4 Address | Subnet Mask | Ring Position | Management IP |
|--------|----------|--------------|-------------|---------------|---------------|
| Switch1 | RING-SW01 | 192.168.4.1 | 255.255.255.0 | Position 1 | 192.168.4.1 |
| Switch2 | RING-SW02 | 192.168.4.2 | 255.255.255.0 | Position 2 | 192.168.4.2 |
| Switch3 | RING-SW03 | 192.168.4.3 | 255.255.255.0 | Position 3 | 192.168.4.3 |
| Switch4 | RING-SW04 | 192.168.4.4 | 255.255.255.0 | Position 4 | 192.168.4.4 |
| PC1 | RING-PC01 | 192.168.4.10 | 255.255.255.0 | SW01 | N/A |
| PC2 | RING-PC02 | 192.168.4.11 | 255.255.255.0 | SW02 | N/A |
| PC3 | RING-PC03 | 192.168.4.12 | 255.255.255.0 | SW03 | N/A |
| PC4 | RING-PC04 | 192.168.4.13 | 255.255.255.0 | SW04 | N/A |

#### IPv6 Configuration
- **Network**: 2001:db8:4::/64
- **Ring Links**: 2001:db8:4:1::/64 to 2001:db8:4:4::/64

| Device | IPv6 Address | Prefix |
|--------|--------------|--------|
| PC1 | 2001:db8:4::10/64 | 64 |
| PC2 | 2001:db8:4::11/64 | 64 |
| PC3 | 2001:db8:4::12/64 | 64 |
| PC4 | 2001:db8:4::13/64 | 64 |

## Implementation Steps

### 1. Physical Layout
1. Place 4 switches in circular arrangement
2. Connect switches in ring: SW01→SW02→SW03→SW04→SW01
3. Connect one PC to each switch
4. Use crossover cables between switches
5. Use straight-through cables for PC connections

### 2. Switch Configuration

#### Basic Switch Setup (Example for SW01)
```cisco
Switch> enable
Switch# configure terminal
Switch(config)# hostname RING-SW01
Switch(config)# interface vlan1
Switch(config-if)# ip address 192.168.4.1 255.255.255.0
Switch(config-if)# no shutdown
```

#### Spanning Tree Configuration
```cisco
Switch(config)# spanning-tree mode rapid-pvst
Switch(config)# spanning-tree vlan 1 priority 4096
Switch(config)# spanning-tree portfast default
```

#### Ring Connections
```cisco
! Connection to next switch in ring
Switch(config)# interface FastEthernet0/23
Switch(config-if)# description "Ring connection to RING-SW02"
Switch(config-if)# no shutdown

! Connection from previous switch in ring
Switch(config)# interface FastEthernet0/24
Switch(config-if)# description "Ring connection from RING-SW04"
Switch(config-if)# no shutdown
```

### 3. Spanning Tree Configuration

#### Root Bridge Selection
```cisco
! Make SW01 the root bridge
Switch(config)# spanning-tree vlan 1 root primary

! Alternative priority method
Switch(config)# spanning-tree vlan 1 priority 0
```

#### Port Roles Configuration
```cisco
! Configure designated ports
Switch(config)# interface FastEthernet0/23
Switch(config-if)# spanning-tree port-priority 128

! Monitor spanning tree
Switch# show spanning-tree
```

## Testing Procedures

### Ring Functionality Testing
- Verify spanning tree convergence
- Test path redundancy
- Simulate link failures
- Measure convergence times

### Connectivity Testing
- Ping tests between all devices
- Verify optimal path selection
- Test broadcast forwarding
- Monitor loop prevention

### Performance Analysis
- Measure latency around ring
- Test bandwidth utilization
- Analyze spanning tree overhead
- Monitor port utilization

## Key Features

### Advantages
- **Fault Tolerance**: Automatic path switching when links fail
- **Equal Access**: All devices have equal access opportunities
- **Predictable Performance**: Known maximum data transmission time
- **Loop Prevention**: Spanning tree prevents broadcast storms

### Disadvantages
- **Single Point of Failure**: Break in ring affects performance
- **Latency**: Data may travel longer paths
- **Complexity**: Spanning tree configuration requirements
- **Troubleshooting**: Harder to isolate problems

## Ring Characteristics

### Token Passing Concepts (Theoretical)
- Deterministic access method
- Collision-free operation
- Fair access to network resources
- Predictable response times

### Modern Implementation
- Ethernet switching with STP
- VLAN support
- Quality of Service (QoS)
- Rapid spanning tree protocol

## Documentation Requirements

### Spanning Tree Information
- Root bridge election results
- Port roles and states
- Convergence times
- Topology changes

### Network Performance
- Path selection verification
- Failover testing results
- Bandwidth measurements
- Latency analysis

## Files in this Directory
- `ring-topology.pkt` - Cisco Packet Tracer file
- `config-backup/` - Switch configurations
- `screenshots/` - Implementation and STP screenshots
- `testing-results.md` - Ring functionality tests
- `spanning-tree-analysis.md` - STP configuration details

---
*Part of NetSimX - CMPG 325 Computer Networks Project*
