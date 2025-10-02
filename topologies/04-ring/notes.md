# Ring Topology Notes

## Implementation Summary
- **Network**: 192.168.4.0/24
- **Devices**: 4 Switches in ring + 8 PCs
- **Protocol**: Spanning Tree Protocol
- **Key Concept**: Loop prevention and redundancy

## Switch Ring Configuration
- RING-SW1 → RING-SW2 → RING-SW3 → RING-SW4 → RING-SW1
- Each switch has 2 PCs connected
- STP will block one link to prevent loops

## Device IPs
- RING-PC01: 192.168.4.10 (SW1)
- RING-PC02: 192.168.4.11 (SW1)
- RING-PC03: 192.168.4.12 (SW2)
- RING-PC04: 192.168.4.13 (SW2)
- RING-PC05: 192.168.4.14 (SW3)
- RING-PC06: 192.168.4.15 (SW3)
- RING-PC07: 192.168.4.16 (SW4)
- RING-PC08: 192.168.4.17 (SW4)

## Testing
- [ ] All PCs can communicate
- [ ] STP blocking port identified
- [ ] Test redundancy with link failure
- [ ] Network converges after failure

## Key Learning Points
- Spanning Tree Protocol operation
- Network redundancy and failover
- Ring topologies in campus networks