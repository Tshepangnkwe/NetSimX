# 🌍 My DNS Configuration Guide

## What I'm Building
For my NetSimX network, I'm setting up DNS (Domain Name System) service so people can access services by hostname instead of having to remember IP addresses. This makes my network much more user-friendly!

## My Server Setup Requirements

### Hardware I'm Using
- **Device Type**: Server-PT (I'll configure this in Packet Tracer)
- **Service**: DNS (Domain Name System)
- **IPv4 Address**: 192.168.100.30 (this will be my DNS server)
- **IPv6 Address**: 2001:db8:100::30/64 (dual-stack configuration)
- **Domain**: netsimx.local (my local domain name)

## How I'm Setting Up DNS Zones

### My Forward Lookup Zones

#### Primary Zone: netsimx.local
This is where I define which IP addresses correspond to which names:
```dns
; SOA Record
netsimx.local.    IN    SOA    dns.netsimx.local. admin.netsimx.local. (
    2025090601    ; Serial
    3600          ; Refresh
    1800          ; Retry
    1209600       ; Expire
    86400         ; Minimum TTL
)

; NS Records
netsimx.local.    IN    NS     dns.netsimx.local.

; A Records
dns               IN    A      192.168.100.30
mail              IN    A      192.168.100.10
web               IN    A      192.168.100.20
dhcp              IN    A      192.168.100.40

; CNAME Records
www               IN    CNAME  web.netsimx.local.
smtp              IN    CNAME  mail.netsimx.local.

; MX Records
netsimx.local.    IN    MX     10 mail.netsimx.local.
```

### Reverse Lookup Zones

#### 192.168.100.in-addr.arpa
```dns
; SOA Record
100.168.192.in-addr.arpa.    IN    SOA    dns.netsimx.local. admin.netsimx.local. (
    2025090601    ; Serial
    3600          ; Refresh
    1800          ; Retry
    1209600       ; Expire
    86400         ; Minimum TTL
)

; PTR Records
10    IN    PTR    mail.netsimx.local.
20    IN    PTR    web.netsimx.local.
30    IN    PTR    dns.netsimx.local.
40    IN    PTR    dhcp.netsimx.local.
```

## Implementation Steps

### 1. Server Setup
1. Deploy Server-PT device
2. Configure static IP address
3. Enable DNS service
4. Configure hostname

### 2. Zone Configuration
1. Create forward lookup zone
2. Add A records for all servers
3. Configure CNAME records
4. Set up MX records for email
5. Create reverse lookup zones

### 3. Client Configuration
- Configure all network devices to use DNS server
- Test name resolution from different network segments
- Verify recursive queries work properly

## Testing Procedures

### DNS Resolution Testing
```bash
# Test forward lookup
nslookup web.netsimx.local 192.168.100.30
nslookup mail.netsimx.local 192.168.100.30

# Test reverse lookup
nslookup 192.168.100.20 192.168.100.30

# Test MX record
nslookup -type=mx netsimx.local 192.168.100.30
```

### Verification Steps
- Forward lookup resolution
- Reverse lookup resolution
- MX record resolution
- CNAME record resolution
- Recursive query functionality

## Files in this Directory
- `dns-server.pkt` - DNS server configuration
- `zone-files/` - DNS zone configuration files
- `testing-results.md` - DNS resolution test results

---
*Part of NetSimX Network Services*
