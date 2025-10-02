# Star Topology Notes

## Implementation Summary
- **Device**: Central Switch-2960
- **PCs**: 6 devices in 3 VLANs
- **Key Concept**: Centralized switching with VLANs

## VLAN Configuration
- **VLAN 10 (Sales)**: 192.168.10.0/24 (Ports Fa0/1-2)
- **VLAN 20 (IT)**: 192.168.20.0/24 (Ports Fa0/3-4)
- **VLAN 30 (Guest)**: 192.168.30.0/24 (Ports Fa0/5-6)

## Device IPs
- STAR-PC01: 192.168.10.10 (VLAN 10)
- STAR-PC02: 192.168.10.11 (VLAN 10)
- STAR-PC03: 192.168.20.10 (VLAN 20)
- STAR-PC04: 192.168.20.11 (VLAN 20)
- STAR-PC05: 192.168.30.10 (VLAN 30)
- STAR-PC06: 192.168.30.11 (VLAN 30)

## Testing
- [ ] Intra-VLAN communication works
- [ ] Inter-VLAN communication blocked
- [ ] VLAN assignments correct

## Key Learning Points
- Network segmentation with VLANs
- Most common modern network design
- Single point of failure at switch