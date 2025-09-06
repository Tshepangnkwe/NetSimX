# Bus Topology Testing Results

## Test Date: [Insert Date]
## Tester: [Your Name]
## Packet Tracer Version: [Version]

---

## Physical Connectivity Tests

### Device Placement Verification
| Device | Position | Connection Status | Cable Type | Hub Port |
|--------|----------|-------------------|------------|----------|
| BUS-PC01 | Position 1 | ✅ Connected | Straight-through | Fa0/1 |
| BUS-PC02 | Position 2 | ✅ Connected | Straight-through | Fa0/2 |
| BUS-PC03 | Position 3 | ✅ Connected | Straight-through | Fa0/3 |
| BUS-PC04 | Position 4 | ✅ Connected | Straight-through | Fa0/4 |
| BUS-PC05 | Position 5 | ✅ Connected | Straight-through | Fa0/5 |

---

## IP Configuration Verification

### IPv4 Configuration Status
| Device | IP Address | Subnet Mask | Gateway | Status |
|--------|------------|-------------|---------|---------|
| BUS-PC01 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 | [ ] Configured |
| BUS-PC02 | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 | [ ] Configured |
| BUS-PC03 | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 | [ ] Configured |
| BUS-PC04 | 192.168.1.13 | 255.255.255.0 | 192.168.1.1 | [ ] Configured |
| BUS-PC05 | 192.168.1.14 | 255.255.255.0 | 192.168.1.1 | [ ] Configured |

### IPv6 Configuration Status
| Device | IPv6 Address | Prefix | Status |
|--------|--------------|--------|---------|
| BUS-PC01 | 2001:db8:1::10/64 | 64 | [ ] Configured |
| BUS-PC02 | 2001:db8:1::11/64 | 64 | [ ] Configured |
| BUS-PC03 | 2001:db8:1::12/64 | 64 | [ ] Configured |
| BUS-PC04 | 2001:db8:1::13/64 | 64 | [ ] Configured |
| BUS-PC05 | 2001:db8:1::14/64 | 64 | [ ] Configured |

---

## Connectivity Testing

### IPv4 Ping Tests
| Source | Destination | IP Address | Result | Response Time | Notes |
|--------|-------------|------------|---------|---------------|-------|
| PC1 | PC2 | 192.168.1.11 | [ ] Success / [ ] Failed | ___ms | |
| PC1 | PC3 | 192.168.1.12 | [ ] Success / [ ] Failed | ___ms | |
| PC1 | PC4 | 192.168.1.13 | [ ] Success / [ ] Failed | ___ms | |
| PC1 | PC5 | 192.168.1.14 | [ ] Success / [ ] Failed | ___ms | |
| PC2 | PC3 | 192.168.1.12 | [ ] Success / [ ] Failed | ___ms | |
| PC3 | PC5 | 192.168.1.14 | [ ] Success / [ ] Failed | ___ms | |

### IPv6 Ping Tests
| Source | Destination | IPv6 Address | Result | Response Time | Notes |
|--------|-------------|--------------|---------|---------------|-------|
| PC1 | PC2 | 2001:db8:1::11 | [ ] Success / [ ] Failed | ___ms | |
| PC1 | PC5 | 2001:db8:1::14 | [ ] Success / [ ] Failed | ___ms | |
| PC3 | PC4 | 2001:db8:1::13 | [ ] Success / [ ] Failed | ___ms | |

---

## Network Discovery Tests

### ARP Table Analysis
**PC1 ARP Table:**
```
[Insert ARP table output from PC1]
```

**PC3 ARP Table:**
```
[Insert ARP table output from PC3]
```

### MAC Address Learning
| Device | MAC Address | Learned From |
|--------|-------------|--------------|
| PC1 | [MAC] | Hub |
| PC2 | [MAC] | Hub |
| PC3 | [MAC] | Hub |
| PC4 | [MAC] | Hub |
| PC5 | [MAC] | Hub |

---

## Bus Topology Characteristics Verification

### Collision Domain Testing
- [ ] **Shared Bandwidth Confirmed**: All devices share 100Mbps
- [ ] **Collision Detection**: CSMA/CD protocol active
- [ ] **Single Broadcast Domain**: All devices receive broadcasts
- [ ] **Hub Functionality**: Central point repeats signals to all ports

### Performance Analysis
- **Bandwidth per Device**: ___Mbps (100Mbps ÷ 5 = 20Mbps theoretical)
- **Latency**: ___ms average
- **Packet Loss**: ___%
- **Collision Rate**: ___% (if measurable)

---

## Security Testing

### Access Control
- [ ] **No Access Control**: All devices can communicate freely
- [ ] **Broadcast Visibility**: All devices see all traffic
- [ ] **Physical Security**: Single point of failure at hub

---

## Troubleshooting Log

### Issues Encountered
| Issue | Description | Solution | Time to Resolve |
|-------|-------------|----------|-----------------|
| 1. | | | |
| 2. | | | |
| 3. | | | |

### Configuration Changes Made
| Device | Original Config | New Config | Reason |
|--------|----------------|------------|---------|
| | | | |

---

## Summary & Conclusions

### Test Results Summary
- **Total Tests Performed**: ___
- **Successful Tests**: ___
- **Failed Tests**: ___
- **Success Rate**: ___%

### Bus Topology Advantages Observed
- [ ] Simple installation and configuration
- [ ] Cost-effective (minimal cables)
- [ ] Easy troubleshooting of physical connections
- [ ] Linear structure easy to understand

### Bus Topology Disadvantages Observed
- [ ] Single point of failure (hub)
- [ ] Shared bandwidth reduces performance
- [ ] All devices in same collision domain
- [ ] Difficult to isolate network problems
- [ ] Limited scalability

### Learning Outcomes
1. **Understanding of Bus Architecture**: [Your observations]
2. **IP Configuration Skills**: [Your experience]
3. **Testing Methodologies**: [What you learned]
4. **Network Troubleshooting**: [Challenges faced]

---

## Next Steps
- [ ] Complete documentation with screenshots
- [ ] Backup all configuration files
- [ ] Update main project checklist
- [ ] Begin Mesh Topology implementation
- [ ] Prepare for hybrid integration

---

**Testing Completed By**: [Your Name]  
**Date**: [Date]  
**Time Taken**: [Duration]  
**Overall Assessment**: [Pass/Fail/Needs Improvement]

*This testing document is part of NetSimX - CMPG 325 Computer Networks Project*
