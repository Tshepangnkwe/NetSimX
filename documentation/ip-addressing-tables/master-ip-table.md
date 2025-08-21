# IP Addressing Master Table

## NetSimX Project - Complete IP Addressing Scheme

### Network Overview
This document contains the complete IP addressing plan for all network topologies in the NetSimX project.

---

## IPv4 Addressing Scheme

### Network Segmentation Strategy
- **Management Network**: 192.168.0.0/24
- **Bus Topology**: 192.168.1.0/24
- **Mesh Topology**: 192.168.2.0/24
- **Star Topology**: 192.168.3.0/24
- **Ring Topology**: 192.168.4.0/24
- **Extended Star**: 192.168.5.0/24
- **Hybrid Network**: 192.168.10.0/24
- **Server Network**: 192.168.100.0/24
- **VLAN 10 (Admin)**: 192.168.110.0/24
- **VLAN 20 (Users)**: 192.168.120.0/24
- **VLAN 30 (Servers)**: 192.168.130.0/24

---

## Bus Topology (192.168.1.0/24)

| Device | Hostname | IPv4 Address | Subnet Mask | Default Gateway | MAC Address | Interface |
|--------|----------|--------------|-------------|-----------------|-------------|-----------|
| PC1 | BUS-PC01 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 | Auto | FastEthernet0 |
| PC2 | BUS-PC02 | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 | Auto | FastEthernet0 |
| PC3 | BUS-PC03 | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 | Auto | FastEthernet0 |
| PC4 | BUS-PC04 | 192.168.1.13 | 255.255.255.0 | 192.168.1.1 | Auto | FastEthernet0 |
| PC5 | BUS-PC05 | 192.168.1.14 | 255.255.255.0 | 192.168.1.1 | Auto | FastEthernet0 |

---

## Mesh Topology (192.168.2.0/24)

| Device | Hostname | IPv4 Address | Subnet Mask | Default Gateway | Interface | Connection Type |
|--------|----------|--------------|-------------|-----------------|-----------|-----------------|
| Router1 | MESH-R01 | 192.168.2.1 | 255.255.255.0 | N/A | Fa0/0 | Hub Router |
| Router2 | MESH-R02 | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 | Fa0/0 | Mesh Node |
| Router3 | MESH-R03 | 192.168.2.3 | 255.255.255.0 | 192.168.2.1 | Fa0/0 | Mesh Node |
| Router4 | MESH-R04 | 192.168.2.4 | 255.255.255.0 | 192.168.2.1 | Fa0/0 | Mesh Node |
| PC1 | MESH-PC01 | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 | Fa0 | End Device |
| PC2 | MESH-PC02 | 192.168.2.11 | 255.255.255.0 | 192.168.2.2 | Fa0 | End Device |

---

## Star Topology (192.168.3.0/24)

| Device | Hostname | IPv4 Address | Subnet Mask | Default Gateway | Interface | Port |
|--------|----------|--------------|-------------|-----------------|-----------|------|
| Switch1 | STAR-SW01 | 192.168.3.1 | 255.255.255.0 | N/A | VLAN1 | Central Switch |
| PC1 | STAR-PC01 | 192.168.3.10 | 255.255.255.0 | 192.168.3.1 | Fa0 | Fa0/1 |
| PC2 | STAR-PC02 | 192.168.3.11 | 255.255.255.0 | 192.168.3.1 | Fa0 | Fa0/2 |
| PC3 | STAR-PC03 | 192.168.3.12 | 255.255.255.0 | 192.168.3.1 | Fa0 | Fa0/3 |
| PC4 | STAR-PC04 | 192.168.3.13 | 255.255.255.0 | 192.168.3.1 | Fa0 | Fa0/4 |
| Server1 | STAR-SRV01 | 192.168.3.100 | 255.255.255.0 | 192.168.3.1 | Fa0 | Fa0/24 |

---

## Ring Topology (192.168.4.0/24)

| Device | Hostname | IPv4 Address | Subnet Mask | Default Gateway | Interface | Ring Position |
|--------|----------|--------------|-------------|-----------------|-----------|---------------|
| Switch1 | RING-SW01 | 192.168.4.1 | 255.255.255.0 | N/A | VLAN1 | Position 1 |
| Switch2 | RING-SW02 | 192.168.4.2 | 255.255.255.0 | N/A | VLAN1 | Position 2 |
| Switch3 | RING-SW03 | 192.168.4.3 | 255.255.255.0 | N/A | VLAN1 | Position 3 |
| Switch4 | RING-SW04 | 192.168.4.4 | 255.255.255.0 | N/A | VLAN1 | Position 4 |
| PC1 | RING-PC01 | 192.168.4.10 | 255.255.255.0 | 192.168.4.1 | Fa0 | SW01 |
| PC2 | RING-PC02 | 192.168.4.11 | 255.255.255.0 | 192.168.4.2 | Fa0 | SW02 |

---

## Extended Star Topology (192.168.5.0/24)

| Device | Hostname | IPv4 Address | Subnet Mask | Default Gateway | Interface | Level |
|--------|----------|--------------|-------------|-----------------|-----------|-------|
| Core-Switch | EXT-CORE-SW | 192.168.5.1 | 255.255.255.0 | N/A | VLAN1 | Core |
| Access-SW1 | EXT-ACC-SW1 | 192.168.5.10 | 255.255.255.0 | 192.168.5.1 | VLAN1 | Access |
| Access-SW2 | EXT-ACC-SW2 | 192.168.5.11 | 255.255.255.0 | 192.168.5.1 | VLAN1 | Access |
| PC1 | EXT-PC01 | 192.168.5.20 | 255.255.255.0 | 192.168.5.1 | Fa0 | End Device |
| PC2 | EXT-PC02 | 192.168.5.21 | 255.255.255.0 | 192.168.5.1 | Fa0 | End Device |

---

## Server Network (192.168.100.0/24)

| Device | Hostname | IPv4 Address | Subnet Mask | Default Gateway | Service | Port |
|--------|----------|--------------|-------------|-----------------|---------|------|
| Email-Server | MAIL-SRV01 | 192.168.100.10 | 255.255.255.0 | 192.168.100.1 | SMTP/POP3 | 25/110 |
| Web-Server | WEB-SRV01 | 192.168.100.20 | 255.255.255.0 | 192.168.100.1 | HTTP/HTTPS | 80/443 |
| DNS-Server | DNS-SRV01 | 192.168.100.30 | 255.255.255.0 | 192.168.100.1 | DNS | 53 |
| DHCP-Server | DHCP-SRV01 | 192.168.100.40 | 255.255.255.0 | 192.168.100.1 | DHCP | 67/68 |

---

## IPv6 Addressing Scheme

### IPv6 Network Plan
- **Global Prefix**: 2001:db8::/32
- **Site Prefix**: 2001:db8:1::/48

### Subnet Allocation
- **Bus Topology**: 2001:db8:1:1::/64
- **Mesh Topology**: 2001:db8:1:2::/64
- **Star Topology**: 2001:db8:1:3::/64
- **Ring Topology**: 2001:db8:1:4::/64
- **Extended Star**: 2001:db8:1:5::/64
- **Hybrid Network**: 2001:db8:1:10::/64
- **Server Network**: 2001:db8:1:100::/64

### IPv6 Address Examples

| Topology | Device | IPv6 Address | Prefix Length |
|----------|--------|--------------|---------------|
| Bus | PC1 | 2001:db8:1:1::10/64 | 64 |
| Bus | PC2 | 2001:db8:1:1::11/64 | 64 |
| Mesh | Router1 | 2001:db8:1:2::1/64 | 64 |
| Star | Switch1 | 2001:db8:1:3::1/64 | 64 |
| Servers | Email | 2001:db8:1:100::10/64 | 64 |

---

## VLAN Configuration

### VLAN Segmentation Plan

| VLAN ID | VLAN Name | IPv4 Network | IPv6 Network | Purpose |
|---------|-----------|--------------|--------------|---------|
| 1 | Default | 192.168.1.0/24 | 2001:db8:1:1::/64 | Default VLAN |
| 10 | Admin | 192.168.110.0/24 | 2001:db8:1:110::/64 | Administrative |
| 20 | Users | 192.168.120.0/24 | 2001:db8:1:120::/64 | End Users |
| 30 | Servers | 192.168.130.0/24 | 2001:db8:1:130::/64 | Server Network |
| 99 | Management | 192.168.199.0/24 | 2001:db8:1:199::/64 | Network Management |

---

## Subnetting Information

### Subnet Calculations
- **Class C Networks**: /24 subnets (254 hosts each)
- **VLSM**: Variable Length Subnet Masking applied
- **Reserved Addresses**: 
  - Network Address: First IP in range
  - Broadcast Address: Last IP in range
  - Gateway: Usually .1 address

### Address Allocation Strategy
- **Network Infrastructure**: .1 - .9
- **Servers**: .10 - .99 or .100 - .199
- **End Devices**: .10 - .254 (depending on topology)
- **Management**: .200 - .254

---

## DNS Configuration

### Domain Structure
- **Primary Domain**: netsimx.local
- **Subdomains**: 
  - admin.netsimx.local
  - users.netsimx.local
  - servers.netsimx.local

### DNS Records
| Record Type | Name | Value | TTL |
|-------------|------|-------|-----|
| A | mail | 192.168.100.10 | 3600 |
| A | web | 192.168.100.20 | 3600 |
| A | dns | 192.168.100.30 | 3600 |
| MX | netsimx.local | mail.netsimx.local | 3600 |
| CNAME | www | web.netsimx.local | 3600 |

---

## DHCP Configuration

### DHCP Pools
| Pool Name | Network | Range Start | Range End | Gateway | DNS |
|-----------|---------|-------------|-----------|---------|-----|
| BUS-POOL | 192.168.1.0/24 | 192.168.1.50 | 192.168.1.200 | 192.168.1.1 | 192.168.100.30 |
| STAR-POOL | 192.168.3.0/24 | 192.168.3.50 | 192.168.3.200 | 192.168.3.1 | 192.168.100.30 |
| USER-VLAN | 192.168.120.0/24 | 192.168.120.50 | 192.168.120.200 | 192.168.120.1 | 192.168.100.30 |

---

*This document is part of the NetSimX project documentation for CMPG 325 Computer Networks.*
*Last Updated: [Current Date]*
