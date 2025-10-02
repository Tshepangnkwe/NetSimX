# Extended Star Topology Notes

## Implementation Summary
- **Core**: Multilayer Switch-3560 with routing
- **Access**: 3 Switch-2960 devices
- **Architecture**: Hierarchical design
- **Key Concept**: Scalable enterprise network

## VLAN Structure
- **VLAN 10 (Floor1)**: 192.168.10.0/24 via ACCESS-SW1
- **VLAN 20 (Floor2)**: 192.168.20.0/24 via ACCESS-SW2
- **VLAN 30 (Floor3)**: 192.168.30.0/24 via ACCESS-SW3

## Inter-VLAN Routing
- Core switch provides routing between VLANs
- Each VLAN has gateway on core switch
- Floor1 Gateway: 192.168.10.1
- Floor2 Gateway: 192.168.20.1
- Floor3 Gateway: 192.168.30.1

## Testing
- [ ] Intra-floor communication works
- [ ] Inter-floor communication via core
- [ ] Routing table shows all VLANs
- [ ] Scalability demonstrated

## Key Learning Points
- Hierarchical network design
- Core/access layer separation
- Inter-VLAN routing configuration
- Enterprise network foundations