# 🕸️ Mesh Topology Implementation Guide

## 📋 Implementation Overview

**Objective**: Create a full mesh topology with OSPF routing demonstrating redundancy, load balancing, and multiple path selection.

**File Name**: `04-mesh-topology.pkt`

## 🎯 Learning Goals

- Understand full mesh connectivity
- Implement OSPF routing protocol
- Demonstrate load balancing
- Test fault tolerance and redundancy

## 🏗️ Network Design

### Physical Layout (Full Mesh)
```
R1 ---- R2
 |   X   |
 |  / \  |
R4 ---- R3
```

### Required Devices
- **4 Routers**: Use `1841` from Network Devices > Routers
- **4 PCs**: Use `PC-PT` from End Devices > PCs
- **Serial cables**: Use `Serial DCE` cables from Connections
- **Straight-through cables**: Use `Copper Straight-Through` cables from Connections

## 🔧 Step-by-Step Implementation

### Step 1: Create New Packet Tracer File
1. Open Cisco Packet Tracer
2. Create new file: `File > New`
3. Save as: `04-mesh-topology.pkt`

### Step 2: Add Devices
1. **Add Routers**:
   - Go to `Network Devices > Routers`
   - Select `1841` router (Cisco 1841 Integrated Services Router)
   - Drag 4 routers to workspace in square formation
   - Label them: `Mesh-R1`, `Mesh-R2`, `Mesh-R3`, `Mesh-R4`
   - **Router Ports Available**:
     - `FastEthernet0/0` and `FastEthernet0/1` (LAN connections)
     - `Serial0/0/0`, `Serial0/0/1`, `Serial0/1/0` (WAN connections)
     - `Console` port (management)
     - `Aux` port (auxiliary/dial-up access)

2. **Add PCs**:
   - Go to `End Devices > PCs`
   - Select `PC-PT`
   - Drag 4 PCs near each router
   - Label them: `Mesh-PC1`, `Mesh-PC2`, `Mesh-PC3`, `Mesh-PC4`

### Step 3: Create Full Mesh Connections

## 🔌 **Understanding Router Ports**

### **Serial Ports (WAN Connections)**:
- **Purpose**: Connect routers over WAN links (point-to-point)
- **Speed**: Typically 64 kbps to 2 Mbps (configurable)
- **Cable Type**: Serial DCE cables (one end DCE, one end DTE)
- **Ports Available**: Serial0/0/0, Serial0/0/1, Serial0/1/0

### **FastEthernet Ports (LAN Connections)**:
- **Purpose**: Connect to local network devices (PCs, switches)
- **Speed**: 100 Mbps full-duplex
- **Cable Type**: Copper Straight-Through cables
- **Ports Available**: FastEthernet0/0, FastEthernet0/1

### **Management Ports**:
- **Console Port**: Direct management access (blue cable)
- **Aux Port**: Remote dial-up access (black cable)

## 🔗 **Detailed Connection Steps**

### **Router-to-Router Serial Connections**:

1. **Connection R1 to R2**:
   - Go to `Connections > Serial DCE`
   - Click `Mesh-R1` → Select `Serial0/0/0` (DCE side)
   - Click `Mesh-R2` → Select `Serial0/0/0` (DTE side)

2. **Connection R1 to R3**:
   - Use `Serial DCE` cable
   - `Mesh-R1` Serial0/0/1 (DCE) → `Mesh-R3` Serial0/0/0 (DTE)

3. **Connection R1 to R4**:
   - Use `Serial DCE` cable
   - `Mesh-R1` Serial0/1/0 (DCE) → `Mesh-R4` Serial0/0/0 (DTE)

4. **Connection R2 to R3**:
   - Use `Serial DCE` cable
   - `Mesh-R2` Serial0/0/1 (DCE) → `Mesh-R3` Serial0/0/1 (DTE)

5. **Connection R2 to R4**:
   - Use `Serial DCE` cable
   - `Mesh-R2` Serial0/1/0 (DCE) → `Mesh-R4` Serial0/0/1 (DTE)

6. **Connection R3 to R4**:
   - Use `Serial DCE` cable
   - `Mesh-R3` Serial0/1/0 (DCE) → `Mesh-R4` Serial0/1/0 (DTE)

### **PC-to-Router FastEthernet Connections**:

1. **PC Connections**:
   - Go to `Connections > Copper Straight-Through`
   - `Mesh-PC1` FastEthernet0 → `Mesh-R1` FastEthernet0/0
   - `Mesh-PC2` FastEthernet0 → `Mesh-R2` FastEthernet0/0
   - `Mesh-PC3` FastEthernet0 → `Mesh-R3` FastEthernet0/0
   - `Mesh-PC4` FastEthernet0 → `Mesh-R4` FastEthernet0/0

### **Connection Verification**:
- **Serial Links**: Should show orange/red initially (not configured)
- **FastEthernet Links**: Should show green dots (auto-negotiation)
- **Total Connections**: 6 serial + 4 ethernet = 10 cables

### Step 4: Detailed Router Configuration

## 🔧 **Router Configuration Process**

### **Access Router CLI**:
1. **Click on Mesh-R1**
2. **Go to CLI tab** (Command Line Interface)
3. **Press Enter** to start configuration

### **Understanding Router Modes**:
- **User EXEC Mode**: `Router>` (limited commands)
- **Privileged EXEC Mode**: `Router#` (full access)
- **Global Configuration Mode**: `Router(config)#` (system-wide config)
- **Interface Configuration Mode**: `Router(config-if)#` (interface-specific)

## 📝 **Complete Mesh-R1 Configuration**:

```cisco
Router>enable
Router#configure terminal

# Set hostname for identification
Router(config)#hostname Mesh-R1

# Configure LAN Interface (FastEthernet0/0)
Router(config)#interface fastethernet 0/0
Router(config-if)#description "LAN Connection to Mesh-PC1"
Router(config-if)#ip address 192.168.1.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit

# Configure WAN Interfaces (Serial connections to other routers)

# Serial 0/0/0 - Connection to Mesh-R2
Router(config)#interface serial 0/0/0
Router(config-if)#description "WAN Link to Mesh-R2"
Router(config-if)#ip address 10.1.12.1 255.255.255.252
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/0/1 - Connection to Mesh-R3
Router(config)#interface serial 0/0/1
Router(config-if)#description "WAN Link to Mesh-R3"
Router(config-if)#ip address 10.1.13.1 255.255.255.252
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/1/0 - Connection to Mesh-R4
Router(config)#interface serial 0/1/0
Router(config-if)#description "WAN Link to Mesh-R4"
Router(config-if)#ip address 10.1.14.1 255.255.255.252
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#exit
```

## 📋 **Configuration Explanations**:

### **Clock Rate Command**:
- **Purpose**: Sets synchronization speed on DCE side of serial link
- **Value**: 64000 = 64 kbps (standard WAN speed)
- **Required**: Only on DCE side (determined by cable type)

### **IP Addressing Scheme**:
- **LAN Networks**: 192.168.X.0/24 (Class C private)
  - R1 LAN: 192.168.1.0/24
  - R2 LAN: 192.168.2.0/24
  - R3 LAN: 192.168.3.0/24
  - R4 LAN: 192.168.4.0/24

- **WAN Point-to-Point Links**: 10.1.XY.0/30 (only 2 hosts needed)
  - R1-R2: 10.1.12.0/30 (.1 and .2 usable)
  - R1-R3: 10.1.13.0/30 (.1 and .2 usable)
  - R1-R4: 10.1.14.0/30 (.1 and .2 usable)
  - R2-R3: 10.1.23.0/30 (.1 and .2 usable)
  - R2-R4: 10.1.24.0/30 (.1 and .2 usable)
  - R3-R4: 10.1.34.0/30 (.1 and .2 usable)

## 📝 **Complete Mesh-R2 Configuration**:

```cisco
Router>enable
Router#configure terminal
Router(config)#hostname Mesh-R2

# LAN Interface
Router(config)#interface fastethernet 0/0
Router(config-if)#description "LAN Connection to Mesh-PC2"
Router(config-if)#ip address 192.168.2.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/0/0 - Connection to Mesh-R1
Router(config)#interface serial 0/0/0
Router(config-if)#description "WAN Link to Mesh-R1"
Router(config-if)#ip address 10.1.12.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/0/1 - Connection to Mesh-R3
Router(config)#interface serial 0/0/1
Router(config-if)#description "WAN Link to Mesh-R3"
Router(config-if)#ip address 10.1.23.1 255.255.255.252
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/1/0 - Connection to Mesh-R4
Router(config)#interface serial 0/1/0
Router(config-if)#description "WAN Link to Mesh-R4"
Router(config-if)#ip address 10.1.24.1 255.255.255.252
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#exit
```

## 📝 **Complete Mesh-R3 Configuration**:

```cisco
Router>enable
Router#configure terminal
Router(config)#hostname Mesh-R3

# LAN Interface
Router(config)#interface fastethernet 0/0
Router(config-if)#description "LAN Connection to Mesh-PC3"
Router(config-if)#ip address 192.168.3.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/0/0 - Connection to Mesh-R1
Router(config)#interface serial 0/0/0
Router(config-if)#description "WAN Link to Mesh-R1"
Router(config-if)#ip address 10.1.13.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/0/1 - Connection to Mesh-R2
Router(config)#interface serial 0/0/1
Router(config-if)#description "WAN Link to Mesh-R2"
Router(config-if)#ip address 10.1.23.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/1/0 - Connection to Mesh-R4
Router(config)#interface serial 0/1/0
Router(config-if)#description "WAN Link to Mesh-R4"
Router(config-if)#ip address 10.1.34.1 255.255.255.252
Router(config-if)#clock rate 64000
Router(config-if)#no shutdown
Router(config-if)#exit
```

## 📝 **Complete Mesh-R4 Configuration**:

```cisco
Router>enable
Router#configure terminal
Router(config)#hostname Mesh-R4

# LAN Interface
Router(config)#interface fastethernet 0/0
Router(config-if)#description "LAN Connection to Mesh-PC4"
Router(config-if)#ip address 192.168.4.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/0/0 - Connection to Mesh-R1
Router(config)#interface serial 0/0/0
Router(config-if)#description "WAN Link to Mesh-R1"
Router(config-if)#ip address 10.1.14.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/0/1 - Connection to Mesh-R2
Router(config)#interface serial 0/0/1
Router(config-if)#description "WAN Link to Mesh-R2"
Router(config-if)#ip address 10.1.24.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit

# Serial 0/1/0 - Connection to Mesh-R3
Router(config)#interface serial 0/1/0
Router(config-if)#description "WAN Link to Mesh-R3"
Router(config-if)#ip address 10.1.34.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit
```

### Step 5: Configure OSPF Routing

**On each router**:
```cisco
Router(config)#router ospf 1
Router(config-router)#network 192.168.1.0 0.0.0.255 area 0
Router(config-router)#network 10.1.12.0 0.0.0.3 area 0
Router(config-router)#network 10.1.13.0 0.0.0.3 area 0
Router(config-router)#network 10.1.14.0 0.0.0.3 area 0
```

### Step 6: Configure PC IP Addresses

- **Mesh-PC1**: 192.168.1.10/24, Gateway: 192.168.1.1
- **Mesh-PC2**: 192.168.2.10/24, Gateway: 192.168.2.1
- **Mesh-PC3**: 192.168.3.10/24, Gateway: 192.168.3.1
- **Mesh-PC4**: 192.168.4.10/24, Gateway: 192.168.4.1

## 🧪 Testing & Validation

### OSPF Verification
```cisco
# Check OSPF neighbors
show ip ospf neighbor

# Check routing table
show ip route

# Check OSPF database
show ip ospf database
```

### Connectivity Testing
1. **Test connectivity between all PCs**
2. **Use traceroute to see path selection**
3. **Verify multiple paths available**

### Load Balancing Test
```cisco
# Check if load balancing is active
show ip route
# Look for multiple equal-cost paths
```

### Fault Tolerance Test
1. **Disconnect one router link**
2. **Verify OSPF reconvergence**
3. **Test connectivity via alternate paths**

## 📊 Key Characteristics to Demonstrate

### 1. Multiple Paths
- **Test**: Traceroute between distant nodes
- **Observation**: Different paths for different destinations
- **Explanation**: Full mesh provides multiple route options

### 2. Load Balancing
- **Test**: Multiple equal-cost paths in routing table
- **Observation**: OSPF can use multiple paths simultaneously
- **Explanation**: Improved bandwidth utilization

### 3. Fast Convergence
- **Test**: Link failure and recovery time
- **Observation**: Quick OSPF reconvergence
- **Explanation**: Redundant paths enable fast recovery

## 📸 Screenshots to Take

1. **Physical Topology**: Full mesh layout
2. **OSPF Neighbors**: Neighbor relationships
3. **Routing Table**: Multiple paths to destinations
4. **Traceroute Results**: Path diversity
5. **Link Failure Test**: Convergence demonstration

## 🔍 Troubleshooting

### Problem: OSPF Neighbors Not Forming
**Solutions**:
- Check interface IP addresses and subnet masks
- Verify OSPF network statements
- Check interface status (up/up)

### Problem: No Load Balancing
**Solutions**:
- Verify equal-cost paths exist
- Check OSPF cost calculations
- Ensure maximum-paths is configured

## ✅ Completion Checklist

- [ ] 4 routers in full mesh configuration
- [ ] All serial interfaces configured and up
- [ ] OSPF running on all routers
- [ ] All PCs can communicate
- [ ] Multiple paths verified in routing table
- [ ] Fault tolerance tested
- [ ] Screenshots documented
- [ ] File saved as `04-mesh-topology.pkt`

---

**Key Learning**: Mesh topology with OSPF provides excellent redundancy and automatic path selection for enterprise networks!