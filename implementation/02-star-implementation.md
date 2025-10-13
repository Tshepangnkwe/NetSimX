# ⭐ Star Topology Implementation Guide

## 📋 Implementation Overview

**Objective**: Create a star topology network demonstrating centralized switching, VLANs, and collision domain separation.

**File Name**: `02-star-topology.pkt`

## 🎯 Learning Goals

- Understand centralized switching concept
- Demonstrate VLAN functionality
- Show collision domain separation
- Implement inter-VLAN routing

## 🏗️ Network Design

### Physical Layout
```
     PC1
      |
PC4--SW1--PC2
      |
     PC3
```

### Required Devices
- **1 Switch**: Use `2960-24TT` from Network Devices > Switches
- **4 PCs**: Use `PC-PT` from End Devices > PCs
- **Straight-through cables**: Use `Copper Straight-Through` cables from Connections

## 🔧 Step-by-Step Implementation

### Step 1: Create New Packet Tracer File
1. Open Cisco Packet Tracer
2. Create new file: `File > New`
3. Save as: `02-star-topology.pkt`

### Step 2: Add Devices
1. **Add Switch**:
   - Go to `Network Devices > Switches`
   - Select `2960-24TT` (Cisco Catalyst 2960)
   - Drag to workspace center
   - Label it: `Star-SW1`

2. **Add PCs**:
   - Go to `End Devices > PCs`
   - Select `PC-PT`
   - Drag 4 PCs around the switch
   - Label them: `Star-PC1`, `Star-PC2`, `Star-PC3`, `Star-PC4`

### Step 3: Connect Devices
1. **Cable Selection**:
   - Go to `Connections` tab at bottom
   - Select `Copper Straight-Through` cable (lightning bolt icon)

2. **Make Connections**:
   - Click on `Star-PC1` → Select `FastEthernet0` port
   - Click on `Star-SW1` → Select `FastEthernet0/1` port
   - Repeat for other PCs:
     - `Star-PC2` FastEthernet0 → `Star-SW1` FastEthernet0/2
     - `Star-PC3` FastEthernet0 → `Star-SW1` FastEthernet0/3
     - `Star-PC4` FastEthernet0 → `Star-SW1` FastEthernet0/4

3. **Verify Connections**:
   - All cable connections should show green dots (link up)
   - If red, check cable type and port selection

### Step 4: Basic IP Configuration

**VLAN 10 (Sales Department)**:
- `Star-PC1`: 192.168.10.10/24
- `Star-PC2`: 192.168.10.11/24

**VLAN 20 (Engineering Department)**:
- `Star-PC3`: 192.168.20.10/24
- `Star-PC4`: 192.168.20.11/24

### Step 5: Configure Switch VLANs

1. **Click on Star-SW1**
2. **Go to CLI tab**
3. **Enter the following commands**:

```cisco
Switch>enable
Switch#configure terminal
Switch(config)#hostname Star-SW1

# Create VLANs
Star-SW1(config)#vlan 10
Star-SW1(config-vlan)#name Sales
Star-SW1(config-vlan)#exit

Star-SW1(config)#vlan 20
Star-SW1(config-vlan)#name Engineering
Star-SW1(config-vlan)#exit

# Assign ports to VLANs
Star-SW1(config)#interface range fastethernet 0/1-2
Star-SW1(config-if-range)#switchport mode access
Star-SW1(config-if-range)#switchport access vlan 10
Star-SW1(config-if-range)#exit

Star-SW1(config)#interface range fastethernet 0/3-4
Star-SW1(config-if-range)#switchport mode access
Star-SW1(config-if-range)#switchport access vlan 20
Star-SW1(config-if-range)#exit
```

### Step 6: Configure PC IP Addresses

**Star-PC1** (VLAN 10):
```
IP Address: 192.168.10.10
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.10.1
```

**Star-PC2** (VLAN 10):
```
IP Address: 192.168.10.11
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.10.1
```

**Star-PC3** (VLAN 20):
```
IP Address: 192.168.20.10
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.20.1
```

**Star-PC4** (VLAN 20):
```
IP Address: 192.168.20.11
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.20.1
```

## 🧪 Testing & Validation

### Intra-VLAN Connectivity Test
1. **From Star-PC1** (VLAN 10):
   - Ping `192.168.10.11` (PC2) - Should work
   - Ping `192.168.20.10` (PC3) - Should fail

2. **From Star-PC3** (VLAN 20):
   - Ping `192.168.20.11` (PC4) - Should work
   - Ping `192.168.10.10` (PC1) - Should fail

### Switch MAC Address Table
1. **Generate traffic** between PCs in same VLAN
2. **Check MAC table**:
   ```cisco
   Star-SW1#show mac address-table
   ```
3. **Observe**: Switch learns MAC addresses per port

### VLAN Verification
```cisco
Star-SW1#show vlan brief
Star-SW1#show interfaces status
```

## 📊 Advanced Configuration (Optional)

### Add Router for Inter-VLAN Routing

1. **Add Router**:
   - Add `1841` router to workspace
   - Label it: `Star-R1`

2. **Configure Router**:
   ```cisco
   Router>enable
   Router#configure terminal
   Router(config)#hostname Star-R1

   # Configure subinterfaces for VLANs
   Router(config)#interface fastethernet 0/0.10
   Router(config-subif)#encapsulation dot1Q 10
   Router(config-subif)#ip address 192.168.10.1 255.255.255.0
   Router(config-subif)#exit

   Router(config)#interface fastethernet 0/0.20
   Router(config-subif)#encapsulation dot1Q 20
   Router(config-subif)#ip address 192.168.20.1 255.255.255.0
   Router(config-subif)#exit

   Router(config)#interface fastethernet 0/0
   Router(config-if)#no shutdown
   ```

3. **Configure Switch Trunk**:
   ```cisco
   Star-SW1(config)#interface fastethernet 0/24
   Star-SW1(config-if)#switchport mode trunk
   Star-SW1(config-if)#switchport trunk allowed vlan 10,20
   ```

## 📸 Screenshots to Take

1. **Network Overview**: Complete star topology
2. **VLAN Configuration**: Switch VLAN table
3. **MAC Address Table**: Learned addresses
4. **Ping Results**: Intra-VLAN and inter-VLAN tests
5. **Interface Status**: Port assignments

## 🔍 Troubleshooting

### Problem: VLAN Communication Fails
**Solutions**:
- Check VLAN assignments: `show vlan brief`
- Verify port configuration: `show interfaces status`
- Ensure correct IP subnets

### Problem: Inter-VLAN Routing Not Working
**Solutions**:
- Check router subinterface configuration
- Verify trunk port configuration
- Confirm default gateway settings on PCs

## 📝 Documentation Notes

### Configuration Summary
```
VLANs: 10 (Sales), 20 (Engineering)
Networks: 192.168.10.0/24, 192.168.20.0/24
Collision Domains: 4 (one per switch port)
Broadcast Domains: 2 (one per VLAN)
```

### Performance Characteristics
```
Bandwidth per Port: 100 Mbps (full-duplex)
Collision Domains: Separate per port
VLAN Isolation: Layer 2 segmentation
Fault Tolerance: Good (isolated ports)
```

## 🎯 Demonstration Points

### For Video Demo (2-3 minutes)
1. **Show Network Layout** (30 seconds)
   - Explain star topology concept
   - Point out central switch

2. **Demonstrate VLAN Separation** (90 seconds)
   - Show intra-VLAN communication
   - Show VLAN isolation
   - Check MAC address table

3. **Explain Switching Benefits** (60 seconds)
   - Collision domain separation
   - Full-duplex communication
   - VLAN flexibility

## ✅ Completion Checklist

- [ ] All 4 PCs connected to switch
- [ ] VLANs created and configured
- [ ] IP addresses configured correctly
- [ ] Intra-VLAN communication working
- [ ] Inter-VLAN isolation demonstrated
- [ ] MAC address table populated
- [ ] Screenshots taken and saved
- [ ] File saved as `02-star-topology.pkt`

## 🔄 Next Steps

After completing star topology:
1. **Save and close** current file
2. **Move to**: [Ring Topology Implementation](03-ring-implementation.md)
3. **Note differences** in fault tolerance approaches

---

**Key Insight**: Star topology with VLANs provides excellent segmentation and performance - foundation of modern enterprise networks!