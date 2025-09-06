# 🌐 My Web Server Configuration Guide

## What I'm Setting Up
This is my guide for setting up HTTP/HTTPS web services as part of my NetSimX project's network services implementation. I'm learning how to host websites on my network!

## My Server Setup Requirements

### What Hardware I'm Using in Packet Tracer
- **Device Type**: Server-PT (I'll drag this from the servers section)
- **Services**: HTTP and HTTPS (web services)
- **Operating System**: Generic Server OS (Packet Tracer simulation)
- **RAM**: 1GB recommended for good performance
- **Storage**: 2GB so I can store web content and files

### How I'm Configuring My Web Server Network
- **IPv4 Address**: 192.168.100.20 (this will be my web server's IP)
- **Subnet Mask**: 255.255.255.0
- **Default Gateway**: 192.168.100.1 (for internet access)
- **DNS Server**: 192.168.100.30 (to resolve domain names)
- **Domain**: web.netsimx.local (my local domain name)

## Implementation Steps

### 1. Basic Server Setup
1. Deploy Server-PT device in server VLAN
2. Configure static IP addressing
3. Enable HTTP and HTTPS services
4. Configure server hostname

### 2. HTTP Service Configuration
```html
<!-- Default web page content -->
<!DOCTYPE html>
<html>
<head>
    <title>NetSimX Web Server</title>
</head>
<body>
    <h1>Welcome to NetSimX Web Server</h1>
    <p>CMPG 325 Computer Networks Project</p>
    <p>Server IP: 192.168.100.20</p>
    <p>Service Status: Online</p>
</body>
</html>
```

### 3. Virtual Hosts Configuration
- **Main Site**: web.netsimx.local
- **Admin Panel**: admin.netsimx.local
- **Test Page**: test.netsimx.local

### 4. Testing Procedures
- HTTP connectivity from all network segments
- DNS resolution verification
- Load testing with multiple clients
- Service availability monitoring

## Files in this Directory
- `web-server.pkt` - Packet Tracer configuration
- `web-content/` - HTML files and resources
- `config-backup/` - Server configuration backup
- `testing-results.md` - Web service test results

---
*Part of NetSimX Network Services*
