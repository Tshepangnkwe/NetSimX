# 📧 My Email Server Configuration

## What I'm Implementing
This is my email server setup for Part II of the CMPG 325 project (worth 20% of my grade). I'm learning how to configure a complete email system from scratch!

## My Server Setup Requirements

### What Hardware I'm Using in Packet Tracer
- **Device Type**: Server-PT (this is what I'll drag into my topology)
- **Services**: SMTP, POP3, and IMAP if Packet Tracer supports it
- **Operating System**: Cisco IOS simulation
- **RAM**: 512MB minimum (I'll check this in the server properties)
- **Storage**: 1GB minimum for storing emails

### How I'm Configuring the Network

#### My Server's IP Configuration
- **IPv4 Address**: 192.168.100.10 (this will be my email server's address)
- **Subnet Mask**: 255.255.255.0
- **Default Gateway**: 192.168.100.1 (so it can reach other networks)
- **DNS Server**: 192.168.100.1 (for resolving domain names)

#### Email Server Settings
- **SMTP Port**: 25
- **POP3 Port**: 110
- **IMAP Port**: 143 (if available)
- **Domain**: netsimx.local

## Implementation Steps

### 1. Server Setup
1. Place Server-PT device in Packet Tracer
2. Configure basic IP settings
3. Enable email services
4. Configure DNS for email domain

### 2. SMTP Configuration
```bash
# Basic SMTP Configuration
service smtp
smtp server enable
smtp domain netsimx.local
```

### 3. User Account Creation
Create email accounts for my project:
- admin@netsimx.local
- tshepang@netsimx.local
- user1@netsimx.local
- support@netsimx.local### 4. Client Configuration
Configure email clients on workstations:
- **Incoming Mail Server**: 192.168.100.10
- **Outgoing Mail Server**: 192.168.100.10
- **Account Type**: POP3 or IMAP
- **Authentication**: Username/Password

## Testing Procedures

### 1. Basic Connectivity
- Ping email server from client machines
- Verify port connectivity (telnet to port 25)
- Check DNS resolution for email domain

### 2. Email Functionality
- Send email between local accounts
- Verify email delivery
- Test email retrieval
- Check email storage

### 3. Client Testing
Test email functionality from multiple clients:
- Send email from PC1 to PC2
- Reply to emails
- Forward messages
- Check email in inbox

## Configuration Files

### Server Configuration
```
hostname EmailServer
!
interface FastEthernet0/0
 ip address 192.168.100.10 255.255.255.0
 no shutdown
!
service smtp
 domain netsimx.local
 enable
!
```

### Client Configuration Example
```
Email Account Settings:
- Email Address: user1@netsimx.local
- Incoming Mail Server: 192.168.100.10
- Incoming Mail Type: POP3
- Outgoing Mail Server: 192.168.100.10
- Username: user1
- Password: password123
```

## Documentation Requirements

### Screenshots Needed
1. Server configuration interface
2. Email service status
3. User account creation
4. Client email configuration
5. Successful email send/receive
6. Email inbox showing received messages

### Configuration Notes
- Document all server settings
- Record user account details
- Note any troubleshooting steps
- Include network topology showing email server

## Troubleshooting

### Common Issues
1. **Connection Refused**: Check if SMTP service is running
2. **Authentication Failed**: Verify username/password
3. **DNS Resolution**: Ensure proper DNS configuration
4. **Port Blocking**: Verify firewall settings

### Diagnostic Commands
```bash
# Server Side
show service smtp
show users
netstat -an

# Client Side  
ping 192.168.100.10
telnet 192.168.100.10 25
nslookup netsimx.local
```

## Integration with Network Topologies

### Placement Strategy
- Include email server in hybrid topology
- Connect to main network infrastructure
- Ensure proper VLAN configuration
- Implement security measures

### Network Services Integration
- **DNS**: Configure MX records
- **DHCP**: Automatic IP assignment
- **Security**: Access control lists
- **Monitoring**: Network performance

## Demo Preparation

### Video Demonstration Points
1. Server setup and configuration
2. Email account creation
3. Client configuration
4. Sending test emails
5. Receiving and reading emails
6. Multiple user testing

### Testing Scenarios
- Internal email communication
- Multiple simultaneous users
- Email with attachments (if supported)
- Error handling demonstration

## Files in this Directory
- `email-server.pkt` - Packet Tracer file with email server
- `server-config.txt` - Server configuration backup
- `client-configs/` - Client configuration examples
- `test-results.md` - Email testing results
- `screenshots/` - Implementation screenshots

---
*Part of NetSimX - CMPG 325 Computer Networks Project*
*Individual Network Feature Configuration - 20% Weight*
