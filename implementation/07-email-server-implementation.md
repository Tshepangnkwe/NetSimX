# 📧 Email Server Implementation Guide

## 📋 Implementation Overview

**Objective**: Configure a complete email system with SMTP, POP3, IMAP services, DNS integration, and multiple client access methods.

**File Name**: `07-email-server.pkt`

## 🎯 Learning Goals

- Understand email server architecture
- Configure SMTP, POP3, and IMAP services
- Implement DNS for email routing
- Test multiple email client configurations

## 🏗️ Network Design

### Email System Architecture
```
    [DNS Server]
         |
    [Email Server]
    SMTP/POP3/IMAP
         |
    [Core Switch]
      /    |    \
  [PC1]  [PC2]  [PC3]
Outlook  Web   Thunderbird
```

### Required Devices
- **1 Email Server**: Use `Server-PT` from End Devices > Servers
- **1 DNS Server**: Use `Server-PT` from End Devices > Servers
- **1 Switch**: Use `2960-24TT` from Network Devices > Switches
- **3 PCs**: Use `PC-PT` from End Devices > PCs
- **1 Router**: Use `1841` from Network Devices > Routers (optional)
- **Straight-through cables**: Use `Copper Straight-Through` cables from Connections

## 🔧 Step-by-Step Implementation

### Step 1: Create New Packet Tracer File
1. Open Cisco Packet Tracer
2. Create new file: `File > New`
3. Save as: `07-email-server.pkt`

### Step 2: Add Devices
1. **Add Servers**:
   - 2 `Server-PT` devices
   - Label them: `Email-Server`, `DNS-Server`

2. **Add Network Equipment**:
   - 1 `2960-24TT` switch: `Email-Switch`
   - 1 `1841` router: `Email-Router` (optional)

3. **Add Client PCs**:
   - 3 `PC-PT` devices
   - Label them: `Outlook-PC`, `Webmail-PC`, `Mobile-PC`

### Step 3: Create Network Connections

**Server Connections**:
- Email-Server to Email-Switch Fa0/1
- DNS-Server to Email-Switch Fa0/2

**Client Connections**:
- Outlook-PC to Email-Switch Fa0/3
- Webmail-PC to Email-Switch Fa0/4
- Mobile-PC to Email-Switch Fa0/5

### Step 4: Configure IP Addressing

**Email-Server**:
- IP Address: 192.168.1.10
- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.1.1
- DNS Server: 192.168.1.20

**DNS-Server**:
- IP Address: 192.168.1.20
- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.1.1

**Client PCs**:
- Outlook-PC: 192.168.1.100/24, Gateway: 192.168.1.1, DNS: 192.168.1.20
- Webmail-PC: 192.168.1.101/24, Gateway: 192.168.1.1, DNS: 192.168.1.20
- Mobile-PC: 192.168.1.102/24, Gateway: 192.168.1.1, DNS: 192.168.1.20

### Step 5: Configure DNS Server

**DNS Server Setup**:
1. Click on DNS-Server
2. Go to Services tab
3. Enable DNS service
4. Add DNS records:

```
Type: A Record
Name: mail.company.com
Address: 192.168.1.10

Type: MX Record
Name: company.com
Mail Server: mail.company.com
Priority: 10

Type: A Record
Name: dns.company.com
Address: 192.168.1.20
```

### Step 6: Configure Email Server Services

**SMTP Service Configuration**:
1. Click on Email-Server
2. Go to Services tab
3. Click on SMTP:
   - Enable SMTP service
   - Domain Name: company.com
   - Check "Enable SMTP Authentication"

**POP3 Service Configuration**:
1. In Services tab, click on POP3:
   - Enable POP3 service
   - Use default port 110

**IMAP Service Configuration**:
1. In Services tab, click on IMAP:
   - Enable IMAP service
   - Use default port 143

**HTTP Service (Webmail)**:
1. In Services tab, click on HTTP:
   - Enable HTTP service
   - Port: 80

### Step 7: Create Email User Accounts

**Add Users on Email Server**:
1. In Email service configuration
2. Add multiple users:

```
User: john.doe
Password: password123
Domain: company.com
Full Email: john.doe@company.com

User: jane.smith
Password: password123
Domain: company.com
Full Email: jane.smith@company.com

User: admin
Password: admin123
Domain: company.com
Full Email: admin@company.com
```

### Step 8: Configure Email Clients

**Outlook-PC Configuration (Desktop Client)**:
1. Click on PC, go to Desktop
2. Open Email Client
3. Configure account:
   - Name: John Doe
   - Email: john.doe@company.com
   - Password: password123
   - Incoming Mail Server: 192.168.1.10
   - Outgoing Mail Server: 192.168.1.10
   - Account Type: POP3

**Webmail-PC Configuration (Web Browser)**:
1. Click on PC, go to Desktop
2. Open Web Browser
3. Navigate to: http://192.168.1.10
4. Login with email credentials

**Mobile-PC Configuration (IMAP)**:
1. Click on PC, go to Desktop
2. Open Email Client
3. Configure account:
   - Name: Jane Smith
   - Email: jane.smith@company.com
   - Password: password123
   - Incoming Mail Server: 192.168.1.10
   - Outgoing Mail Server: 192.168.1.10
   - Account Type: IMAP

## 🧪 Testing & Validation

### Email Server Status Check
1. **Check Service Status**:
   - SMTP service running on port 25
   - POP3 service running on port 110
   - IMAP service running on port 143
   - HTTP service running on port 80

### DNS Resolution Testing
1. **Test DNS from PC**:
   - Command Prompt: `nslookup mail.company.com`
   - Should resolve to 192.168.1.10

### Email Flow Testing

**Test 1: Send Email via Desktop Client**:
1. From Outlook-PC, compose email to jane.smith@company.com
2. Send email
3. Check delivery on Mobile-PC (IMAP client)

**Test 2: Send Email via Webmail**:
1. From Webmail-PC, login via browser
2. Compose email to admin@company.com
3. Send email
4. Check delivery in admin mailbox

**Test 3: Reply to Email**:
1. Reply to received email
2. Verify two-way communication

## 📊 Email Protocols Demonstration

### SMTP (Outgoing Mail)
- **Port**: 25
- **Function**: Send emails from clients to server
- **Test**: Send email from any client
- **Verification**: Check server logs

### POP3 (Download Mail)
- **Port**: 110
- **Function**: Download emails to local client
- **Test**: Check mail on Outlook-PC
- **Verification**: Email removed from server

### IMAP (Sync Mail)
- **Port**: 143
- **Function**: Synchronize emails across devices
- **Test**: Check mail on Mobile-PC
- **Verification**: Email remains on server

### HTTP (Webmail)
- **Port**: 80
- **Function**: Web-based email access
- **Test**: Access via browser
- **Verification**: Web interface functionality

## 📸 Screenshots to Take

1. **Network Topology**: Complete email system layout
2. **DNS Configuration**: DNS records and settings
3. **Email Server Services**: SMTP, POP3, IMAP status
4. **User Accounts**: Created email accounts
5. **Desktop Email Client**: Configured and working
6. **Webmail Interface**: Browser-based email access
7. **Email Delivery**: Successful email transmission
8. **Multiple Protocols**: Different client types working

## 🔍 Troubleshooting

### Problem: Cannot Resolve mail.company.com
**Solutions**:
- Check DNS server configuration
- Verify DNS records (A and MX)
- Check PC DNS settings

### Problem: Cannot Send Email
**Solutions**:
- Verify SMTP service is running
- Check email client SMTP settings
- Confirm user authentication

### Problem: Cannot Receive Email
**Solutions**:
- Check POP3/IMAP service status
- Verify email account exists
- Check client configuration

### Problem: Webmail Not Working
**Solutions**:
- Verify HTTP service is enabled
- Check web browser URL
- Confirm server IP address

## 🔐 Security Considerations

### Basic Security Setup
1. **Strong Passwords**: Use complex passwords for email accounts
2. **Service Hardening**: Disable unnecessary services
3. **Access Control**: Limit administrative access

### Authentication Testing
1. **Valid Credentials**: Test with correct passwords
2. **Invalid Credentials**: Verify rejection of wrong passwords
3. **Account Lockout**: Test multiple failed attempts

## ✅ Completion Checklist

- [ ] DNS server configured with email records
- [ ] Email server with SMTP, POP3, IMAP services
- [ ] Multiple user accounts created
- [ ] Desktop email client configured (POP3)
- [ ] Webmail access working (HTTP)
- [ ] Mobile client configured (IMAP)
- [ ] Email sending successful
- [ ] Email receiving successful
- [ ] DNS resolution working
- [ ] Multiple protocol types demonstrated
- [ ] Screenshots documented
- [ ] File saved as `07-email-server.pkt`

## 📋 Email Test Matrix

| From Client | To Account | Protocol | Status |
|-------------|------------|----------|---------|
| Outlook-PC | jane.smith@company.com | SMTP/POP3 | ✓ |
| Webmail-PC | admin@company.com | HTTP | ✓ |
| Mobile-PC | john.doe@company.com | SMTP/IMAP | ✓ |

---

**Key Learning**: Email server implementation demonstrates complete messaging infrastructure with multiple protocols and client types, essential for enterprise communications!