# 🔄 Ring Topology Implementation Guide

## 📋 Implementation Overview

**Objective**: Create a ring topology network demonstrating redundant paths, Spanning Tree Protocol, and fault tolerance.

**File Name**: `03-ring-topology.pkt`

## 🎯 Learning Goals

- Understand redundant path concept
- Demonstrate Spanning Tree Protocol (STP)
- Show loop prevention mechanisms
- Test fault tolerance capabilities

## 🏗️ Network Design

### Physical Layout (Logical Ring using Switches)
```
    SW1 ---- SW2
     |        |
     |        |
    SW4 ---- SW3
```

### Required Devices
- **4 Switches**: Use `2960-24TT` from Network Devices > Switches
- **4 PCs**: Use `PC-PT` from End Devices > PCs
- **Straight-through cables**: Use `Copper Straight-Through` cables from Connections

## 🔧 Step-by-Step Implementation

### Step 1: Create New Packet Tracer File
1. Open Cisco Packet Tracer
2. Create new file: `File > New`
3. Save as: `03-ring-topology.pkt`

### Step 2: Add Devices
1. **Add Switches**:
   - Add 4 `2960-24TT` switches
   - Label them: `Ring-SW1`, `Ring-SW2`, `Ring-SW3`, `Ring-SW4`

2. **Add PCs**:
   - Add 4 `PC-PT` devices
   - Label them: `Ring-PC1`, `Ring-PC2`, `Ring-PC3`, `Ring-PC4`

### Step 3: Create Ring Connections
1. **Switch-to-Switch Links**:
   - `Ring-SW1` Fa0/23 to `Ring-SW2` Fa0/23
   - `Ring-SW2` Fa0/24 to `Ring-SW3` Fa0/23
   - `Ring-SW3` Fa0/24 to `Ring-SW4` Fa0/23
   - `Ring-SW4` Fa0/24 to `Ring-SW1` Fa0/24

2. **PC Connections**:
   - `Ring-PC1` to `Ring-SW1` Fa0/1
   - `Ring-PC2` to `Ring-SW2` Fa0/1
   - `Ring-PC3` to `Ring-SW3` Fa0/1
   - `Ring-PC4` to `Ring-SW4` Fa0/1

### Step 4: Configure Spanning Tree

**On each switch, configure STP**:

```cisco
Switch>enable
Switch#configure terminal
Switch(config)#hostname Ring-SW1
Ring-SW1(config)#spanning-tree mode pvst+
Ring-SW1(config)#spanning-tree vlan 1 priority 4096
```

**Repeat for other switches with different priorities**:
- Ring-SW1: priority 4096 (Root Bridge)
- Ring-SW2: priority 8192
- Ring-SW3: priority 12288
- Ring-SW4: priority 16384

### Step 5: Configure IP Addresses

**All devices in same subnet**:
- `Ring-PC1`: 192.168.3.10/24
- `Ring-PC2`: 192.168.3.11/24
- `Ring-PC3`: 192.168.3.12/24
- `Ring-PC4`: 192.168.3.13/24

### Step 6: Verify Spanning Tree Operation

```cisco
Ring-SW1#show spanning-tree
Ring-SW1#show spanning-tree summary
Ring-SW1#show spanning-tree interface fastethernet 0/23
```

## 🧪 Testing & Validation

### Basic Connectivity Test
1. **Test connectivity between all PCs**
2. **Verify one path is blocked by STP**
3. **Check spanning tree topology**

### Fault Tolerance Test
1. **Disconnect one inter-switch link**
2. **Observe STP reconvergence**
3. **Verify connectivity is restored**
4. **Measure convergence time**

### Spanning Tree Analysis
```cisco
# View spanning tree status
show spanning-tree

# Check port states
show spanning-tree interface fastethernet 0/23

# Monitor convergence
show spanning-tree summary
```

## 📊 Key Characteristics to Demonstrate

### 1. Loop Prevention
- **Test**: Check which ports are blocked
- **Observation**: STP blocks one link to prevent loops
- **Explanation**: Creates loop-free topology

### 2. Fault Tolerance
- **Test**: Remove one connection
- **Observation**: Network reconverges automatically
- **Explanation**: Backup paths activated

### 3. Root Bridge Election
- **Test**: Check spanning tree topology
- **Observation**: Lowest priority switch becomes root
- **Explanation**: Centralized tree structure

## 📸 Screenshots to Take

1. **Physical Topology**: Ring layout with connections
2. **Spanning Tree Output**: STP status and port states
3. **Root Bridge**: Root bridge election results
4. **Port States**: Forwarding and blocking ports
5. **Convergence Test**: Before and after link failure

## 🔍 Troubleshooting

### Problem: Loops in Network
**Solution**: Verify STP is enabled and configured properly

### Problem: Slow Convergence
**Solution**: Use Rapid Spanning Tree (RSTP) instead of classic STP

### Problem: Wrong Root Bridge
**Solution**: Adjust bridge priorities to control root election

## ✅ Completion Checklist

- [ ] 4 switches connected in ring topology
- [ ] Spanning Tree Protocol configured
- [ ] One port blocked to prevent loops
- [ ] Connectivity test successful
- [ ] Fault tolerance demonstrated
- [ ] Screenshots documented
- [ ] File saved as `03-ring-topology.pkt`

---

**Key Learning**: Ring topology provides redundancy through STP, balancing fault tolerance with loop prevention!