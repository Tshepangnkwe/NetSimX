# 🔗 Hybrid Topology Implementation Guide

## 📋 Implementation Overview

**Objective**: Create a hybrid topology combining star, ring, and mesh elements with OSPF routing, VLANs, and advanced network services.

**File Name**: `06-hybrid-topology.pkt`

## 🎯 Learning Goals

- Combine multiple topology types
- Implement advanced routing protocols
- Demonstrate real-world network design
- Integrate multiple network services

## 🏗️ Network Design

### Physical Layout (Hybrid)
```
        Core Ring
    R1 -------- R2
     |          |
     |    +-----+
     |    |
    SW1  SW2 (Star clusters)
   /  |  |  \
PC1 PC2 PC3 PC4

     |
   Mesh WAN
     |
   Internet
```

### Required Devices
- **3 Routers**: Use `1841` from Network Devices > Routers
- **3 Switches**: Use `2960-24TT` from Network Devices > Switches
- **6 PCs**: Use `PC-PT` from End Devices > PCs
- **1 Server**: Use `Server-PT` from End Devices > Servers
- **Serial cables**: Use `Serial DCE` cables from Connections
- **Straight-through cables**: Use `Copper Straight-Through` cables from Connections

## 🔧 Step-by-Step Implementation

### Step 1: Create New Packet Tracer File
1. Open Cisco Packet Tracer
2. Create new file: `File > New`
3. Save as: `06-hybrid-topology.pkt`

### Step 2: Add Devices
1. **Add Routers**:
   - 3 `1841` routers: `Core-R1`, `Core-R2`, `WAN-R3`

2. **Add Switches**:
   - 3 `2960-24TT` switches: `Dept-SW1`, `Dept-SW2`, `Server-SW3`

3. **Add End Devices**:
   - 6 PCs: `HR-PC1`, `HR-PC2`, `Finance-PC1`, `Finance-PC2`, `Admin-PC1`, `Admin-PC2`
   - 1 Server: `Web-Server`

### Step 3: Create Hybrid Connections

**Core Ring (Serial)**:
- Core-R1 S0/0/0 to Core-R2 S0/0/0
- Core-R2 S0/0/1 to WAN-R3 S0/0/0
- WAN-R3 S0/0/1 to Core-R1 S0/0/1

**Star Clusters (FastEthernet)**:
- Core-R1 Fa0/0 to Dept-SW1 Fa0/24
- Core-R2 Fa0/0 to Dept-SW2 Fa0/24
- WAN-R3 Fa0/0 to Server-SW3 Fa0/24

**Access Connections**:
- HR-PC1, HR-PC2 to Dept-SW1
- Finance-PC1, Finance-PC2 to Dept-SW2
- Admin-PC1, Admin-PC2, Web-Server to Server-SW3

### Step 4: Configure Core Ring Network

**Core-R1 Configuration**:
```cisco
Router>enable
Router#configure terminal
Router(config)#hostname Core-R1

# LAN Interface (HR Department)
Router(config)#interface fastethernet 0/0
Router(config-if)#ip address 192.168.10.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit

# Ring Interface to R2
Router(config)#interface serial 0/0/0
Router(config-if)#ip address 10.1.12.1 255.255.255.252
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#exit

# Ring Interface to R3
Router(config)#interface serial 0/0/1
Router(config-if)#ip address 10.1.13.1 255.255.255.252
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#exit

# OSPF Configuration
Router(config)#router ospf 1
Router(config-router)#router-id 1.1.1.1
Router(config-router)#network 192.168.10.0 0.0.0.255 area 0
Router(config-router)#network 10.1.12.0 0.0.0.3 area 0
Router(config-router)#network 10.1.13.0 0.0.0.3 area 0
```

**Core-R2 Configuration**:
```cisco
Router>enable
Router#configure terminal
Router(config)#hostname Core-R2

# LAN Interface (Finance Department)
Router(config)#interface fastethernet 0/0
Router(config-if)#ip address 192.168.20.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit

# Ring Interface to R1
Router(config)#interface serial 0/0/0
Router(config-if)#ip address 10.1.12.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit

# Ring Interface to R3
Router(config)#interface serial 0/0/1
Router(config-if)#ip address 10.1.23.1 255.255.255.252
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#exit

# OSPF Configuration
Router(config)#router ospf 1
Router(config-router)#router-id 2.2.2.2
Router(config-router)#network 192.168.20.0 0.0.0.255 area 0
Router(config-router)#network 10.1.12.0 0.0.0.3 area 0
Router(config-router)#network 10.1.23.0 0.0.0.3 area 0
```

**WAN-R3 Configuration**:
```cisco
Router>enable
Router#configure terminal
Router(config)#hostname WAN-R3

# LAN Interface (Server/Admin)
Router(config)#interface fastethernet 0/0
Router(config-if)#ip address 192.168.30.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit

# Ring Interface to R2
Router(config)#interface serial 0/0/0
Router(config-if)#ip address 10.1.23.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit

# Ring Interface to R1
Router(config)#interface serial 0/0/1
Router(config-if)#ip address 10.1.13.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit

# OSPF Configuration
Router(config)#router ospf 1
Router(config-router)#router-id 3.3.3.3
Router(config-router)#network 192.168.30.0 0.0.0.255 area 0
Router(config-router)#network 10.1.23.0 0.0.0.3 area 0
Router(config-router)#network 10.1.13.0 0.0.0.3 area 0
```

### Step 5: Configure Switch VLANs

**Dept-SW1 (HR Department)**:
```cisco
Switch>enable
Switch#configure terminal
Switch(config)#hostname Dept-SW1

# Create HR VLAN
Switch(config)#vlan 10
Switch(config-vlan)#name HR
Switch(config-vlan)#exit

# Configure access ports
Switch(config)#interface range fastethernet 0/1-10
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan 10
Switch(config-if-range)#no shutdown
Switch(config-if-range)#exit

# Configure uplink to router
Switch(config)#interface fastethernet 0/24
Switch(config-if)#switchport mode access
Switch(config-if)#no shutdown
```

**Similar configuration for Dept-SW2 (Finance) and Server-SW3 (Admin/Servers)**

### Step 6: Configure End Device IP Addresses

**HR Department (192.168.10.0/24)**:
- HR-PC1: 192.168.10.10/24, Gateway: 192.168.10.1
- HR-PC2: 192.168.10.11/24, Gateway: 192.168.10.1

**Finance Department (192.168.20.0/24)**:
- Finance-PC1: 192.168.20.10/24, Gateway: 192.168.20.1
- Finance-PC2: 192.168.20.11/24, Gateway: 192.168.20.1

**Admin/Server (192.168.30.0/24)**:
- Admin-PC1: 192.168.30.10/24, Gateway: 192.168.30.1
- Admin-PC2: 192.168.30.11/24, Gateway: 192.168.30.1
- Web-Server: 192.168.30.50/24, Gateway: 192.168.30.1

### Step 7: Configure Server Services

**Web-Server Configuration**:
1. **HTTP Service**:
   - Enable HTTP service
   - Create simple web page
   - Test access from different departments

2. **DNS Service** (Optional):
   - Configure DNS server
   - Create A records for internal hosts
   - Set as DNS server for PCs

## 🧪 Testing & Validation

### OSPF Ring Verification
```cisco
# Check OSPF neighbors
show ip ospf neighbor

# Check routing table
show ip route ospf

# Check OSPF topology
show ip ospf database
```

### Connectivity Matrix Testing
```
From/To    HR    Finance  Admin  Server
HR         ✓     Via R1   Via R1  Via R1
Finance    Via R2   ✓     Via R2  Via R2
Admin      Via R3  Via R3   ✓      ✓
```

### Redundancy Testing
1. **Disable R1-R2 link**
2. **Verify alternative path via R3**
3. **Check convergence time**

## 📊 Key Characteristics to Demonstrate

### 1. Topology Convergence
- **Ring**: Core router connectivity
- **Star**: Department access layers
- **Mesh**: OSPF route redundancy
- **Hierarchy**: Logical network organization

### 2. Load Distribution
- **Test**: Multiple paths between departments
- **Observation**: OSPF load balancing
- **Explanation**: Efficient bandwidth utilization

### 3. Fault Tolerance
- **Test**: Link failures and recovery
- **Observation**: Automatic rerouting
- **Explanation**: Network resilience

### 4. Service Integration
- **Test**: Web server access from all departments
- **Observation**: Application layer connectivity
- **Explanation**: End-to-end service delivery

## 📸 Screenshots to Take

1. **Complete Topology**: Full hybrid layout
2. **OSPF Neighbors**: All router relationships
3. **Routing Tables**: Path diversity demonstration
4. **Department Communication**: Inter-department connectivity
5. **Server Access**: Web service from multiple clients
6. **Fault Recovery**: Link failure simulation

## 🔍 Troubleshooting

### Problem: OSPF Convergence Issues
**Solutions**:
- Check router IDs are unique
- Verify area consistency
- Check interface types and costs

### Problem: Inter-Department Communication Fails
**Solutions**:
- Check OSPF route propagation
- Verify routing table entries
- Test physical connectivity

### Problem: Server Access Issues
**Solutions**:
- Check server IP configuration
- Verify service status
- Test routing to server subnet

## ✅ Completion Checklist

- [ ] Ring topology core network established
- [ ] Star clusters configured for each department
- [ ] OSPF routing protocol operational
- [ ] All departments can communicate
- [ ] Server services accessible
- [ ] Redundancy demonstrated
- [ ] Load balancing verified
- [ ] Fault tolerance tested
- [ ] Screenshots documented
- [ ] File saved as `06-hybrid-topology.pkt`

---

**Key Learning**: Hybrid topology demonstrates real-world network design combining multiple approaches for optimal performance, redundancy, and scalability!