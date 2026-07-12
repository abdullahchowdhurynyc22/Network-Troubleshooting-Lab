# Enterprise Network Troubleshooting Lab

A hands-on enterprise networking lab that demonstrates structured troubleshooting in a simulated business environment.

The goal of this project was to diagnose and resolve DNS and hostname resolution issues while verifying that the rest of the network infrastructure was functioning correctly.

---

## Lab Environment

| Device | Role | IP Address |
|---------|------|------------|
| pfSense Firewall | Gateway / Firewall | 192.168.10.1 |
| Windows Server 2025 | Active Directory / DNS | 192.168.10.20 |
| Windows 11 Client | Workstation | 192.168.10.10 |
| Ubuntu Server | Linux Server | 192.168.10.30 |
| Ubuntu Desktop | Linux Workstation | 192.168.10.40 |

**Domain:** `lab.local`

**Virtualization:** UTM

---

## Technologies Used

- Windows Server 2025
- Active Directory
- DNS
- Windows 11
- Ubuntu Server
- Ubuntu Desktop
- pfSense Firewall
- TCP/IP Networking

---

## Problem

The Windows client could reach other devices on the network, but DNS wasn't working.

### Symptoms

- `nslookup google.com` failed
- Websites would not load by name
- Internal hostnames could not be resolved
- Ping by IP address worked normally

This showed that the network was working, but DNS was not.

---

## Troubleshooting Steps

- Verified IP configuration
- Tested network connectivity
- Confirmed gateway access
- Verified the DNS server was online
- Reviewed firewall status
- Checked routing
- Tested DNS resolution
- Verified Linux network connectivity
- Reviewed DNS forwarders
- Identified the incorrect DNS configuration
- Applied the fix
- Tested everything again

---

## Root Cause

The Windows client was using the wrong DNS server.

**Incorrect DNS**

```
192.168.10.99
```

Because of this:

- External DNS failed
- Internal hostname resolution failed
- Websites could not be reached by name

During testing, I also found that the Ubuntu Server didn't have a DNS host record.

I created a new DNS record:

```
Hostname: ubuntusrv
IP Address: 192.168.10.30
```

---

## Resolution

Updated the Windows client's DNS settings.

**Correct DNS Configuration**

```
Preferred DNS: 192.168.10.20
Alternate DNS: 8.8.8.8
```

Also:

- Verified DNS forwarders
- Confirmed pfSense connectivity
- Added the missing Ubuntu DNS record

---

## Validation

After the changes:

- ✅ `nslookup google.com` worked
- ✅ `ping google.com` worked
- ✅ `ping ubuntusrv` worked
- ✅ Internal hostname resolution worked
- ✅ External DNS worked
- ✅ Network connectivity was fully restored

---

## Skills Demonstrated

- Enterprise network troubleshooting
- DNS troubleshooting
- Windows networking
- Linux networking
- Active Directory DNS
- Firewall verification
- Root cause analysis
- Network validation

