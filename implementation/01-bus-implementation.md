# 🚌 Bus Topology Implementation Guide

## 📋 Implementation Overview

**Objective**: Create a bus topology network demonstrating shared medium communication and CSMA/CD protocol operation.

**File Name**: `01-bus-topology.pkt`

## 🎯 Learning Goals

- Understand shared medium concept
- Demonstrate collision domains
- Show bandwidth sharing effects
- Implement basic connectivity

## 🏗️ Network Design

### Physical Layout
```
PC1 ---- Hub ---- PC2
         |
         PC3
         |
         PC4
```

### Required Devices
- **1 Hub**: Use `Hub-PT` (Generic Hub) from Network Devices > Hubs
- **4 PCs**: Use `PC-PT` from End Devices > PCs  
- **Straight-through cables**: Use `Copper Straight-Through` cables from Connections

## 🔧 Step-by-Step Implementation

### Step 1: Create New Packet Tracer File
1. Open Cisco Packet Tracer
2. Create new file: `File > New`
3. Save as: `01-bus-topology.pkt`

### Step 2: Add Devices
1. **Add Hub**:
   - Go to `Network Devices > Hubs`
   - Select `Hub-PT` (Generic Hub)
   - Drag to workspace center
   - Label it: `Bus-Hub1`

2. **Add PCs**:
   - Go to `End Devices > PCs`
   - Select `PC-PT`
   - Drag 4 PCs around the hub
   - Label them: `Bus-PC1`, `Bus-PC2`, `Bus-PC3`, `Bus-PC4`

### Step 3: Connect Devices
1. **Cable Selection**:
   - Go to `Connections` tab at bottom
   - Select `Copper Straight-Through` cable (lightning bolt icon)

2. **Make Connections**:
   - Click on `Bus-PC1` → Select `FastEthernet0` port
   - Click on `Bus-Hub1` → Select `FastEthernet0/1` port
   - Repeat for other PCs:
     - `Bus-PC2` FastEthernet0 → `Bus-Hub1` FastEthernet0/2
     - `Bus-PC3` FastEthernet0 → `Bus-Hub1` FastEthernet0/3
     - `Bus-PC4` FastEthernet0 → `Bus-Hub1` FastEthernet0/4

3. **Verify Connections**:
   - All cable connections should show green dots (link up)
   - If red, check cable type and port selection

### Step 4: Configure IP Addresses

**Bus-PC1**:
```
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
```

**Bus-PC2**:
```
IP Address: 192.168.1.11
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
```

**Bus-PC3**:
```
IP Address: 192.168.1.12
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
```

**Bus-PC4**:
```
IP Address: 192.168.1.13
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
```

### Step 5: Configuration Procedure
1. **Click on PC1**
2. **Go to Desktop > IP Configuration**
3. **Select Static**
4. **Enter IP details as above**
5. **Repeat for all PCs**

## 🧪 Testing & Validation

### Basic Connectivity Test
1. **From Bus-PC1**:
   - Open `Command Prompt`
   - Test: `ping 192.168.1.11` (to PC2)
   - Test: `ping 192.168.1.12` (to PC3)
   - Test: `ping 192.168.1.13` (to PC4)

2. **Expected Results**:
   - All pings should be successful
   - Shows shared medium connectivity

### Collision Domain Analysis
1. **Switch to Simulation Mode**:
   - Click `Simulation` tab
   - Add `ICMP` in Event List

2. **Generate Traffic**:
   - Send ping from PC1 to PC2
   - Simultaneously send ping from PC3 to PC4
   - Observe collision behavior

3. **Expected Behavior**:
   - All devices receive all frames
   - Collisions occur with simultaneous transmission
   - Single collision domain for entire network

## 📊 Key Characteristics to Demonstrate

### 1. Shared Medium
- **Test**: Send traffic between any two PCs
- **Observation**: All devices see the traffic
- **Explanation**: Hub forwards all frames to all ports

### 2. Single Collision Domain
- **Test**: Generate simultaneous traffic
- **Observation**: Collisions occur, requiring retransmission
- **Explanation**: CSMA/CD protocol in action

### 3. Bandwidth Sharing
- **Test**: Multiple simultaneous communications
- **Observation**: Reduced effective bandwidth per device
- **Explanation**: 10 Mbps shared among all devices

## 📸 Screenshots to Take

1. **Network Overview**: Complete topology layout
2. **PC Configuration**: IP configuration screen
3. **Ping Results**: Successful connectivity tests
4. **Simulation Mode**: Collision domain visualization
5. **Hub LED Indicators**: Activity lights during traffic

## 🔍 Troubleshooting

### Problem: Ping Fails
**Possible Causes**:
- Incorrect IP configuration
- Wrong cable type used
- Interface not enabled

**Solutions**:
- Verify IP addresses in same subnet
- Use straight-through cables only
- Check interface status in device config

### Problem: No Collisions Visible
**Possible Causes**:
- Not in simulation mode
- ICMP not selected in event list
- Traffic not simultaneous enough

**Solutions**:
- Switch to simulation mode
- Add ICMP to filtered events
- Generate traffic from multiple sources quickly

## 📝 Documentation Notes

### Configuration Summary
```
Network: 192.168.1.0/24
Subnet Mask: 255.255.255.0
Total Devices: 4 PCs + 1 Hub
Collision Domains: 1 (entire network)
Broadcast Domains: 1 (entire network)
```

### Performance Characteristics
```
Theoretical Bandwidth: 10 Mbps
Effective Bandwidth: 10 Mbps ÷ number of active devices
Collision Probability: Increases with more devices
Fault Tolerance: Poor (hub failure affects all)
```

## 🎯 Demonstration Points

### For Video Demo (2-3 minutes)
1. **Show Network Layout** (30 seconds)
   - Explain bus topology concept
   - Point out shared hub

2. **Demonstrate Connectivity** (60 seconds)
   - Ping between different PCs
   - Show successful communication

3. **Show Shared Medium** (60 seconds)
   - Use simulation mode
   - Generate traffic from multiple sources
   - Explain collision behavior

4. **Explain Characteristics** (30 seconds)
   - Single collision domain
   - Bandwidth sharing
   - Fault tolerance issues

## ✅ Completion Checklist

- [ ] All 4 PCs properly connected to hub
- [ ] IP addresses configured correctly
- [ ] Ping tests successful between all devices
- [ ] Collision domain behavior demonstrated
- [ ] Screenshots taken and saved
- [ ] Configuration notes documented
- [ ] File saved as `01-bus-topology.pkt`

## 🔄 Next Steps

After completing bus topology:
1. **Save and close** current file
2. **Move to**: [Star Topology Implementation](02-star-implementation.md)
3. **Apply lessons learned** from bus topology limitations

---

**Remember**: Bus topology is simple but has significant limitations. Use this implementation to understand why modern networks moved to switched topologies!