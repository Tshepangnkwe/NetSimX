# 📊 Master IP Addressing Table

This document contains all IP addresses used across my NetSimX project topologies.

## IPv4 Address Summary

### Bus Topology (192.168.1.0/24)
| Device | IP Address | Subnet Mask | Gateway | Purpose |
|--------|------------|-------------|---------|---------|
| BUS-PC01 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 | Workstation |
| BUS-PC02 | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 | Workstation |
| BUS-PC03 | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 | Workstation |
| BUS-PC04 | 192.168.1.13 | 255.255.255.0 | 192.168.1.1 | Workstation |
| BUS-PC05 | 192.168.1.14 | 255.255.255.0 | 192.168.1.1 | Workstation |

### Mesh Topology (10.1.0.0/16)
| Connection | Device | Interface | IP Address | Subnet |
|------------|--------|-----------|------------|---------|
| R1-R2 | MESH-R1 | S0/0/0 | 10.1.12.1 | /30 |
| R1-R2 | MESH-R2 | S0/0/0 | 10.1.12.2 | /30 |
| R1-R3 | MESH-R1 | S0/0/1 | 10.1.13.1 | /30 |
| R1-R3 | MESH-R3 | S0/0/0 | 10.1.13.2 | /30 |
| R1-R4 | MESH-R1 | S0/1/0 | 10.1.14.1 | /30 |
| R1-R4 | MESH-R4 | S0/0/0 | 10.1.14.2 | /30 |
| R2-R3 | MESH-R2 | S0/0/1 | 10.1.23.1 | /30 |
| R2-R3 | MESH-R3 | S0/0/1 | 10.1.23.2 | /30 |
| R2-R4 | MESH-R2 | S0/1/0 | 10.1.24.1 | /30 |
| R2-R4 | MESH-R4 | S0/0/1 | 10.1.24.2 | /30 |
| R3-R4 | MESH-R3 | S0/1/0 | 10.1.34.1 | /30 |
| R3-R4 | MESH-R4 | S0/1/0 | 10.1.34.2 | /30 |

### Star Topology VLANs
| VLAN | Network | Device | IP Address | Gateway |
|------|---------|--------|------------|---------|
| 10 (Sales) | 192.168.10.0/24 | STAR-PC01 | 192.168.10.10 | 192.168.10.1 |
| 10 (Sales) | 192.168.10.0/24 | STAR-PC02 | 192.168.10.11 | 192.168.10.1 |
| 20 (IT) | 192.168.20.0/24 | STAR-PC03 | 192.168.20.10 | 192.168.20.1 |
| 20 (IT) | 192.168.20.0/24 | STAR-PC04 | 192.168.20.11 | 192.168.20.1 |
| 30 (Guest) | 192.168.30.0/24 | STAR-PC05 | 192.168.30.10 | 192.168.30.1 |
| 30 (Guest) | 192.168.30.0/24 | STAR-PC06 | 192.168.30.11 | 192.168.30.1 |

### Ring Topology (192.168.4.0/24)
| Device | IP Address | Subnet Mask | Gateway | Switch |
|--------|------------|-------------|---------|---------|
| RING-PC01 | 192.168.4.10 | 255.255.255.0 | 192.168.4.1 | RING-SW1 |
| RING-PC02 | 192.168.4.11 | 255.255.255.0 | 192.168.4.1 | RING-SW1 |
| RING-PC03 | 192.168.4.12 | 255.255.255.0 | 192.168.4.1 | RING-SW2 |
| RING-PC04 | 192.168.4.13 | 255.255.255.0 | 192.168.4.1 | RING-SW2 |
| RING-PC05 | 192.168.4.14 | 255.255.255.0 | 192.168.4.1 | RING-SW3 |
| RING-PC06 | 192.168.4.15 | 255.255.255.0 | 192.168.4.1 | RING-SW3 |
| RING-PC07 | 192.168.4.16 | 255.255.255.0 | 192.168.4.1 | RING-SW4 |
| RING-PC08 | 192.168.4.17 | 255.255.255.0 | 192.168.4.1 | RING-SW4 |

### Extended Star Topology
| VLAN | Network | Device | IP Address | Access Switch |
|------|---------|--------|------------|---------------|
| 10 (Floor1) | 192.168.10.0/24 | EXT-PC01 | 192.168.10.10 | ACCESS-SW1 |
| 10 (Floor1) | 192.168.10.0/24 | EXT-PC02 | 192.168.10.11 | ACCESS-SW1 |
| 10 (Floor1) | 192.168.10.0/24 | EXT-PC03 | 192.168.10.12 | ACCESS-SW1 |
| 20 (Floor2) | 192.168.20.0/24 | EXT-PC04 | 192.168.20.10 | ACCESS-SW2 |
| 20 (Floor2) | 192.168.20.0/24 | EXT-PC05 | 192.168.20.11 | ACCESS-SW2 |
| 20 (Floor2) | 192.168.20.0/24 | EXT-PC06 | 192.168.20.12 | ACCESS-SW2 |
| 30 (Floor3) | 192.168.30.0/24 | EXT-PC07 | 192.168.30.10 | ACCESS-SW3 |
| 30 (Floor3) | 192.168.30.0/24 | EXT-PC08 | 192.168.30.11 | ACCESS-SW3 |

### Network Services (192.168.100.0/24)
| Service | Device | IP Address | Purpose |
|---------|--------|------------|---------|
| Email Server | EMAIL-SERVER | 192.168.100.10 | SMTP/POP3/IMAP |
| DNS Server | DNS-SERVER | 192.168.100.30 | Domain Resolution |
| DHCP Server | DHCP-SERVER | 192.168.100.40 | IP Assignment |
| Web Server | WEB-SERVER | 192.168.100.20 | HTTP/HTTPS |

## IPv6 Addressing (If Required)

### Bus Topology IPv6
| Device | IPv6 Address | Prefix |
|--------|--------------|--------|
| BUS-PC01 | 2001:db8:1::10/64 | 64 |
| BUS-PC02 | 2001:db8:1::11/64 | 64 |
| BUS-PC03 | 2001:db8:1::12/64 | 64 |
| BUS-PC04 | 2001:db8:1::13/64 | 64 |
| BUS-PC05 | 2001:db8:1::14/64 | 64 |

## Subnet Summary

| Topology | Network | Subnet Mask | Usable IPs | Purpose |
|----------|---------|-------------|------------|---------|
| Bus | 192.168.1.0/24 | 255.255.255.0 | 254 | Shared bus network |
| Mesh Links | 10.1.0.0/16 | Various /30 | 2 each | Point-to-point router links |
| Star VLANs | 192.168.10-30.0/24 | 255.255.255.0 | 254 each | Departmental networks |
| Ring | 192.168.4.0/24 | 255.255.255.0 | 254 | Ring backbone network |
| Extended Star | 192.168.10-30.0/24 | 255.255.255.0 | 254 each | Floor-based networks |
| Services | 192.168.100.0/24 | 255.255.255.0 | 254 | Server infrastructure |

## VLAN Configuration Summary

| VLAN ID | Name | Purpose | Networks |
|---------|------|---------|----------|
| 10 | Sales/Floor1 | Department/Floor segregation | 192.168.10.0/24 |
| 20 | IT/Floor2 | Department/Floor segregation | 192.168.20.0/24 |
| 30 | Guest/Floor3 | Department/Floor segregation | 192.168.30.0/24 |
| 100 | Management | Switch/Router management | 192.168.100.0/24 |

## DNS Records (netsimx.local domain)

| Type | Name | Target | Purpose |
|------|------|--------|---------|
| A | mail.netsimx.local | 192.168.100.10 | Email server |
| A | www.netsimx.local | 192.168.100.20 | Web server |
| A | dns.netsimx.local | 192.168.100.30 | DNS server |
| MX | netsimx.local | mail.netsimx.local | Mail routing |

---

*This table will be updated as I implement each topology and test connectivity.*