# My Bus Topology Implementation Checklist

## 🎯 Goal: Get my first topology working (12/100 marks)

This is my step-by-step plan to implement the bus topology. I'm breaking it down into phases so I don't get overwhelmed and can track my progress.

### Phase 1: Physical Design (25% of Bus Topology marks)
This is where I actually build the network in Packet Tracer:
- [ ] **Open Cisco Packet Tracer**
- [ ] **Place Devices:**
  - [ ] Add 5 Generic PCs from End Devices
  - [ ] Arrange them in a line like a real bus topology would look
  - [ ] Name them: BUS-PC01, BUS-PC02, BUS-PC03, BUS-PC04, BUS-PC05
- [ ] **Connect Everything:**
  - [ ] Use a Hub-PT device as the backbone (simulates the bus cable)
  - [ ] Connect all PCs to hub using straight-through cables
  - [ ] Make sure all connections show green dots (means they're working)
- [ ] **Save My Work:** `bus-topology.pkt` in the right folder

### Phase 2: IPv4 Configuration (25% of Bus Topology marks)
- [ ] **Configure PC1 (BUS-PC01):**
  - [ ] IP: 192.168.1.10
  - [ ] Subnet: 255.255.255.0
  - [ ] Gateway: 192.168.1.1
- [ ] **Configure PC2 (BUS-PC02):**
  - [ ] IP: 192.168.1.11
  - [ ] Subnet: 255.255.255.0
  - [ ] Gateway: 192.168.1.1
- [ ] **Configure PC3 (BUS-PC03):**
  - [ ] IP: 192.168.1.12
  - [ ] Subnet: 255.255.255.0
  - [ ] Gateway: 192.168.1.1
- [ ] **Configure PC4 (BUS-PC04):**
  - [ ] IP: 192.168.1.13
  - [ ] Subnet: 255.255.255.0
  - [ ] Gateway: 192.168.1.1
- [ ] **Configure PC5 (BUS-PC05):**
  - [ ] IP: 192.168.1.14
  - [ ] Subnet: 255.255.255.0
  - [ ] Gateway: 192.168.1.1

### Phase 3: IPv6 Configuration (15% of Bus Topology marks)
- [ ] **Configure IPv6 on PC1:** 2001:db8:1::10/64
- [ ] **Configure IPv6 on PC2:** 2001:db8:1::11/64
- [ ] **Configure IPv6 on PC3:** 2001:db8:1::12/64
- [ ] **Configure IPv6 on PC4:** 2001:db8:1::13/64
- [ ] **Configure IPv6 on PC5:** 2001:db8:1::14/64

### Phase 4: Testing & Validation (20% of Bus Topology marks)
- [ ] **IPv4 Connectivity Tests:**
  - [ ] PC1 ping PC2 (192.168.1.11)
  - [ ] PC1 ping PC3 (192.168.1.12)
  - [ ] PC1 ping PC4 (192.168.1.13)
  - [ ] PC1 ping PC5 (192.168.1.14)
  - [ ] PC3 ping PC5 (192.168.1.14)
- [ ] **IPv6 Connectivity Tests:**
  - [ ] PC1 ping PC2 (2001:db8:1::11)
  - [ ] PC1 ping PC5 (2001:db8:1::14)
- [ ] **Network Discovery:**
  - [ ] Check ARP tables on all PCs
  - [ ] Verify MAC address learning
- [ ] **Performance Testing:**
  - [ ] Test bandwidth sharing
  - [ ] Observe collision domain behavior

### Phase 5: Documentation (15% of Bus Topology marks)
- [ ] **Screenshots Required:**
  - [ ] Complete topology overview
  - [ ] IP configuration on each PC
  - [ ] Successful ping tests (IPv4)
  - [ ] Successful ping tests (IPv6)
  - [ ] ARP table entries
  - [ ] Hub status and port information
- [ ] **Configuration Backup:**
  - [ ] Export configurations from each PC
  - [ ] Save in `config-backup/` folder
- [ ] **Testing Results:**
  - [ ] Document all ping test results
  - [ ] Create testing summary report

## 🔧 **Detailed Configuration Steps**

### PC Configuration in Packet Tracer:
1. **Click on PC** → **Desktop** → **IP Configuration**
2. **Select Static** instead of DHCP
3. **Enter IP settings** as per the table above
4. **Click on Command Prompt** for testing

### IPv6 Configuration:
1. **Command Prompt** → Type: `ipv6config /ipv6 [address]/64`
2. **Example for PC1:** `ipv6config /ipv6 2001:db8:1::10/64`

### Testing Commands:
```bash
# IPv4 Testing
ping 192.168.1.11
ping 192.168.1.12

# IPv6 Testing  
ping 2001:db8:1::11
ping 2001:db8:1::12

# Network Information
ipconfig /all
arp -a
```

## 📸 **Screenshot Checklist**
- [ ] `01-topology-overview.png` - Complete network layout
- [ ] `02-pc1-ipv4-config.png` - PC1 IP configuration
- [ ] `03-pc2-ipv4-config.png` - PC2 IP configuration  
- [ ] `04-pc3-ipv4-config.png` - PC3 IP configuration
- [ ] `05-ping-test-ipv4.png` - Successful IPv4 ping
- [ ] `06-ping-test-ipv6.png` - Successful IPv6 ping
- [ ] `07-arp-table.png` - ARP table showing MAC addresses
- [ ] `08-hub-status.png` - Hub port status and activity

## ⏰ **Time Estimate**
- **Physical Setup:** 30 minutes
- **IP Configuration:** 45 minutes  
- **Testing:** 30 minutes
- **Documentation:** 45 minutes
- **Total:** ~2.5 hours

## 🎯 **Success Criteria**
- All PCs can ping each other via IPv4 ✓
- IPv6 connectivity working ✓
- Proper documentation with screenshots ✓
- Configuration files backed up ✓
- Hub shows proper activity ✓

---
**Next Step:** After completing this, move to Mesh Topology
**Progress:** 1/6 topologies (12/100 marks potential)
