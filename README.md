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

# Lab Baseline
<br><img width="406" height="659" alt="Image" src="https://github.com/user-attachments/assets/46026722-5735-4589-9be3-5c9fac6fd8cb" /></br>

<br><img width="420" height="318" alt="Image" src="https://github.com/user-attachments/assets/834bb3b1-1958-4590-bbde-2f41f6856dfa" /></br>


---

# Problem Reproduction
<br><img width="413" height="453" alt="Image" src="https://github.com/user-attachments/assets/6766dbf1-9a88-4e53-b52b-7741755e9bf3" /></br>

<br><img width="412" height="309" alt="Image" src="https://github.com/user-attachments/assets/bce2834b-fda1-4db0-855c-323a641365ef" /></br>


---

# Diagnostic Investigation
<br><img width="405" height="612" alt="Image" src="https://github.com/user-attachments/assets/d747a287-4de2-46c8-ba74-ce7fc59741d0" /></br>

<br><img width="412" height="256" alt="Image" src="https://github.com/user-attachments/assets/46b42d0a-dfca-4835-94ec-65cd874cd245" /></br>


---

# Infrastructure Verification

<br><img width="407" height="625" alt="Image" src="https://github.com/user-attachments/assets/a871c513-6511-41c1-9fe3-9470d8690030" /><br>

<br><img width="412" height="307" alt="Image" src="https://github.com/user-attachments/assets/5333ab78-52cd-485d-ab15-9292faf6c807" /></br>

---

# Root Cause and Resolution
<br><img width="408" height="611" alt="Image" src="https://github.com/user-attachments/assets/246ac7c6-c31e-4a0f-bdf2-485c4f035e11" /></br>


<br><img width="379" height="350" alt="Image" src="https://github.com/user-attachments/assets/e2a56045-e356-4a4d-8713-4c4db0fc4b81" /></br>
