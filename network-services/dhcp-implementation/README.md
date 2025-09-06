# 🔧 My DHCP Implementation Guide

## What I'm Building
For my NetSimX project, I'm setting up DHCP (Dynamic Host Configuration Protocol) service so devices can automatically get their IP addresses and network settings. No more manually configuring every single device!

## My Server Setup Requirements

### Hardware I'm Using
- **Device Type**: Server-PT or Router with DHCP service (I'll decide which works better)
- **Service**: DHCP Server
- **IPv4 Address**: 192.168.100.40 (this will be my DHCP server's IP)
- **Scope**: All network segments (every topology will get automatic IPs)
- **Lease Duration**: 24 hours (86400 seconds) so devices keep their IPs for a full day

## How I'm Setting Up My DHCP Pools

### My Pool Definitions

#### Bus Topology Pool
This is how I'll set up automatic IPs for my bus topology:
```cisco
ip dhcp pool BUS_POOL
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 192.168.100.30
 lease 1 0 0
 domain-name netsimx.local
```

#### Star Topology Pool
```cisco
ip dhcp pool STAR_POOL
 network 192.168.3.0 255.255.255.0
 default-router 192.168.3.1
 dns-server 192.168.100.30
 lease 1 0 0
 domain-name netsimx.local
```

#### Extended Star Pools
```cisco
ip dhcp pool EXT_STAR_VLAN10
 network 192.168.5.16 255.255.255.240
 default-router 192.168.5.17
 dns-server 192.168.100.30
 option 66 ascii "192.168.100.40"

ip dhcp pool EXT_STAR_VLAN20
 network 192.168.5.80 255.255.255.240
 default-router 192.168.5.81
 dns-server 192.168.100.30
```

#### Hybrid Network Pools
```cisco
ip dhcp pool HYBRID_VLAN10
 network 192.168.10.0 255.255.255.192
 default-router 192.168.10.1
 dns-server 192.168.100.30

ip dhcp pool HYBRID_VLAN20
 network 192.168.10.64 255.255.255.192
 default-router 192.168.10.65
 dns-server 192.168.100.30
```

### Reserved Addresses
```cisco
! Exclude server and infrastructure IPs
ip dhcp excluded-address 192.168.1.1 192.168.1.9
ip dhcp excluded-address 192.168.3.1 192.168.3.9
ip dhcp excluded-address 192.168.5.1 192.168.5.15
ip dhcp excluded-address 192.168.10.1 192.168.10.9
ip dhcp excluded-address 192.168.100.1 192.168.100.50
```

## DHCP Options Configuration

### Standard Options
- **Option 1**: Subnet Mask
- **Option 3**: Default Gateway
- **Option 6**: DNS Server
- **Option 15**: Domain Name
- **Option 51**: Lease Time
- **Option 66**: TFTP Server (for network booting)

### Custom Options
```cisco
! Time server option
ip dhcp pool ALL_NETWORKS
 option 42 ip 192.168.100.50

! NTP server option
ip dhcp pool ALL_NETWORKS
 option 4 ip 192.168.100.51
```

## Implementation Steps

### 1. Server Deployment
1. Deploy DHCP server in server VLAN
2. Configure static IP address
3. Enable DHCP service
4. Configure hostname and domain

### 2. Pool Configuration
1. Create DHCP pools for each network segment
2. Configure scope and exclusions
3. Set default gateway and DNS options
4. Define lease duration

### 3. Relay Agent Configuration
```cisco
! On router interfaces serving remote subnets
interface FastEthernet0/1
 ip helper-address 192.168.100.40
```

### 4. Monitoring and Management
- Monitor lease assignments
- Check pool utilization
- Manage reservations
- Monitor lease expiration

## DHCP Lease Management

### Lease States
1. **Available**: IP available for assignment
2. **Offered**: IP offered to client
3. **Assigned**: IP assigned and in use
4. **Expired**: Lease has expired

### Lease Process
1. **DHCP Discover**: Client broadcasts for DHCP server
2. **DHCP Offer**: Server offers IP configuration
3. **DHCP Request**: Client requests specific IP
4. **DHCP Acknowledge**: Server confirms assignment

## Testing Procedures

### Client Testing
```bash
# Release current IP
ipconfig /release

# Request new IP
ipconfig /renew

# Display current configuration
ipconfig /all

# Show DHCP lease information
ipconfig /displaydns
```

### Server Testing
```cisco
! Show DHCP bindings
show ip dhcp binding

! Show DHCP pool statistics
show ip dhcp pool

! Show DHCP conflicts
show ip dhcp conflict

! Clear DHCP bindings
clear ip dhcp binding *
```

## Troubleshooting Common Issues

### Client Not Getting IP
1. Check DHCP service is running
2. Verify pool has available addresses
3. Check DHCP relay configuration
4. Verify network connectivity to DHCP server

### IP Address Conflicts
1. Check for static IP conflicts
2. Verify exclusion ranges
3. Clear conflicted bindings
4. Check for rogue DHCP servers

### Lease Problems
1. Check lease duration settings
2. Verify pool utilization
3. Monitor lease expiration
4. Check client renewal process

## Security Considerations

### DHCP Security Features
```cisco
! DHCP snooping on switches
ip dhcp snooping
ip dhcp snooping vlan 10,20,30

! Trusted interfaces
interface FastEthernet0/24
 ip dhcp snooping trust

! Rate limiting
ip dhcp snooping limit rate 10
```

### Access Control
- Limit DHCP server access
- Monitor for unauthorized DHCP servers
- Implement port security on access switches
- Use MAC address reservations for critical devices

## Performance Monitoring

### Key Metrics
- Pool utilization percentage
- Lease assignment rate
- Renewal success rate
- Response time to DHCP requests

### Monitoring Commands
```cisco
! Pool statistics
show ip dhcp pool statistics

! Server statistics
show ip dhcp server statistics

! Binding information
show ip dhcp binding | include Active
```

## Integration with Other Services

### DNS Integration
- Automatic DNS record updates
- Hostname registration
- FQDN assignment
- Reverse DNS updates

### Network Monitoring
- DHCP pool alerts
- Lease expiration warnings
- Conflict detection
- Performance monitoring

## Documentation Requirements

### Configuration Documentation
- DHCP pool configurations
- Exclusion ranges
- Option assignments
- Relay agent configurations

### Operational Documentation
- Lease assignment procedures
- Troubleshooting guides
- Performance baselines
- Security configurations

## Files in this Directory
- `dhcp-server.pkt` - DHCP server configuration
- `pool-configs/` - Individual pool configuration files
- `monitoring-scripts/` - DHCP monitoring tools
- `testing-results.md` - DHCP functionality test results
- `troubleshooting-guide.md` - Common issues and solutions

---
*Part of NetSimX Network Services*
