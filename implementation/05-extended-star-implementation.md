# 🌟 Extended Star Topology Implementation Guide

## 📋 Implementation Overview

**Objective**: Create an extended star topology with multiple star networks connected through a backbone switch, implementing VLANs and inter-VLAN routing.

**File Name**: `05-extended-star-topology.pkt`

## 🎯 Learning Goals

- Understand hierarchical network design
- Implement VLAN segmentation
- Configure inter-VLAN routing
- Demonstrate scalable network architecture

## 🏗️ Network Design

### Physical Layout (Extended Star)
```
Central-Switch (Core)
      |
   -------
   |     |
SW1    SW2
 |      |
PC1    PC3
PC2    PC4
```

### Required Devices
- **1 Core Switch**: Use `2960-24TT` from Network Devices > Switches
- **2 Access Switches**: Use `2960-24TT` from Network Devices > Switches
- **1 Router**: Use `1841` from Network Devices > Routers
- **4 PCs**: Use `PC-PT` from End Devices > PCs
- **Straight-through cables**: Use `Copper Straight-Through` cables from Connections

## 🔧 Step-by-Step Implementation

### Step 1: Create New Packet Tracer File
1. Open Cisco Packet Tracer
2. Create new file: `File > New`
3. Save as: `05-extended-star-topology.pkt`

### Step 2: Add Devices
1. **Add Switches**:
   - Add 3 `2960-24TT` switches
   - Label them: `Core-Switch`, `Access-SW1`, `Access-SW2`

2. **Add Router**:
   - Add 1 `1841` router
   - Label it: `InterVLAN-Router`

3. **Add PCs**:
   - Add 4 `PC-PT` devices
   - Label them: `Sales-PC1`, `Sales-PC2`, `IT-PC1`, `IT-PC2`

### Step 3: Create Connections

**Backbone Connections**:
- Core-Switch Fa0/1 to InterVLAN-Router Fa0/0
- Core-Switch Fa0/2 to Access-SW1 Fa0/24
- Core-Switch Fa0/3 to Access-SW2 Fa0/24

**Access Connections**:
- Access-SW1 Fa0/1 to Sales-PC1
- Access-SW1 Fa0/2 to Sales-PC2
- Access-SW2 Fa0/1 to IT-PC1
- Access-SW2 Fa0/2 to IT-PC2

### Step 4: Configure VLANs

**Core-Switch Configuration**:
```cisco
Switch>enable
Switch#configure terminal
Switch(config)#hostname Core-Switch

# Create VLANs
Switch(config)#vlan 10
Switch(config-vlan)#name Sales
Switch(config-vlan)#exit

Switch(config)#vlan 20
Switch(config-vlan)#name IT
Switch(config-vlan)#exit

# Configure trunk to router
Switch(config)#interface fastethernet 0/1
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk allowed vlan 10,20
Switch(config-if)#no shutdown
Switch(config-if)#exit

# Configure trunks to access switches
Switch(config)#interface fastethernet 0/2
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk allowed vlan 10,20
Switch(config-if)#no shutdown
Switch(config-if)#exit

Switch(config)#interface fastethernet 0/3
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk allowed vlan 10,20
Switch(config-if)#no shutdown
```

**Access-SW1 Configuration (Sales Department)**:
```cisco
Switch>enable
Switch#configure terminal
Switch(config)#hostname Access-SW1

# Create VLANs
Switch(config)#vlan 10
Switch(config-vlan)#name Sales
Switch(config-vlan)#exit

# Configure access ports
Switch(config)#interface range fastethernet 0/1-2
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan 10
Switch(config-if-range)#no shutdown
Switch(config-if-range)#exit

# Configure trunk to core
Switch(config)#interface fastethernet 0/24
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk allowed vlan 10,20
Switch(config-if)#no shutdown
```

**Access-SW2 Configuration (IT Department)**:
```cisco
Switch>enable
Switch#configure terminal
Switch(config)#hostname Access-SW2

# Create VLANs
Switch(config)#vlan 20
Switch(config-vlan)#name IT
Switch(config-vlan)#exit

# Configure access ports
Switch(config)#interface range fastethernet 0/1-2
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan 20
Switch(config-if-range)#no shutdown
Switch(config-if-range)#exit

# Configure trunk to core
Switch(config)#interface fastethernet 0/24
Switch(config-if)#switchport mode trunk
Switch(config-if)#switchport trunk allowed vlan 10,20
Switch(config-if)#no shutdown
```

### Step 5: Configure Inter-VLAN Routing

**Router Configuration**:
```cisco
Router>enable
Router#configure terminal
Router(config)#hostname InterVLAN-Router

# Configure subinterfaces for VLANs
Router(config)#interface fastethernet 0/0
Router(config-if)#no shutdown
Router(config-if)#exit

# VLAN 10 subinterface
Router(config)#interface fastethernet 0/0.10
Router(config-subif)#encapsulation dot1Q 10
Router(config-subif)#ip address 192.168.10.1 255.255.255.0
Router(config-subif)#no shutdown
Router(config-subif)#exit

# VLAN 20 subinterface
Router(config)#interface fastethernet 0/0.20
Router(config-subif)#encapsulation dot1Q 20
Router(config-subif)#ip address 192.168.20.1 255.255.255.0
Router(config-subif)#no shutdown
```

### Step 6: Configure PC IP Addresses

**Sales Department (VLAN 10)**:
- **Sales-PC1**: 192.168.10.10/24, Gateway: 192.168.10.1
- **Sales-PC2**: 192.168.10.11/24, Gateway: 192.168.10.1

**IT Department (VLAN 20)**:
- **IT-PC1**: 192.168.20.10/24, Gateway: 192.168.20.1
- **IT-PC2**: 192.168.20.11/24, Gateway: 192.168.20.1

## 🧪 Testing & Validation

### VLAN Verification
```cisco
# Check VLAN configuration
show vlan brief

# Check trunk status
show interfaces trunk

# Check VLAN interface status
show interfaces vlan 10
show interfaces vlan 20
```

### Connectivity Testing
1. **Intra-VLAN communication**:
   - Sales-PC1 to Sales-PC2 (should work)
   - IT-PC1 to IT-PC2 (should work)

2. **Inter-VLAN communication**:
   - Sales-PC1 to IT-PC1 (should work via router)
   - Verify routing through different VLANs

### Spanning Tree Verification
```cisco
# Check spanning tree status
show spanning-tree

# Verify root bridge
show spanning-tree root
```

## 📊 Key Characteristics to Demonstrate

### 1. VLAN Segmentation
- **Test**: PC communication within VLANs
- **Observation**: Broadcast domain separation
- **Explanation**: VLANs provide logical network segmentation

### 2. Inter-VLAN Routing
- **Test**: Communication between different VLANs
- **Observation**: Router facilitates VLAN communication
- **Explanation**: Layer 3 routing between Layer 2 domains

### 3. Hierarchical Design
- **Test**: Scalability demonstration
- **Observation**: Easy addition of new access switches
- **Explanation**: Core-access model supports growth

### 4. Trunk Links
- **Test**: VLAN traffic over single physical link
- **Observation**: Multiple VLANs traverse trunk ports
- **Explanation**: Efficient use of physical connections

## 📸 Screenshots to Take

1. **Physical Topology**: Extended star layout
2. **VLAN Configuration**: VLAN brief output
3. **Trunk Status**: Trunk interface status
4. **Routing Table**: Inter-VLAN routes
5. **PC Communication**: Successful ping tests

## 🔍 Troubleshooting

### Problem: Inter-VLAN Communication Fails
**Solutions**:
- Check subinterface configuration
- Verify VLAN tagging (dot1Q)
- Check default gateway on PCs

### Problem: VLAN Not Working
**Solutions**:
- Verify VLAN creation on all switches
- Check port VLAN assignments
- Verify trunk configuration

### Problem: Trunk Link Issues
**Solutions**:
- Check trunk mode on both ends
- Verify allowed VLAN list
- Check native VLAN configuration

## ✅ Completion Checklist

- [ ] Core and access switches configured
- [ ] VLANs created and assigned
- [ ] Trunk links established
- [ ] Inter-VLAN routing configured
- [ ] All PCs have connectivity
- [ ] Intra-VLAN communication verified
- [ ] Inter-VLAN communication verified
- [ ] Screenshots documented
- [ ] File saved as `05-extended-star-topology.pkt`

---

**Key Learning**: Extended star topology with VLANs provides scalable, organized network architecture suitable for enterprise environments!