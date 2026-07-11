# Network-Troubleshooting-Lab


## Project Overview
This lab demonstrates hands-on, structured troubleshooting across Windows and Linux systems in a small business network. It covers diagnosing and resolving common operational issues like slow performance, network connectivity drops, and remote access failures.

---

## Lab Environment
* **Domain Name:** lab.local
* **Subnet:** 192.168.10.0/24

| Device Name | Operating System | IP Address | Role / Function |
| :--- | :--- | :--- | :--- |
| pfSense | pfSense Firewall | 192.168.10.1 | Default Gateway |
| WIN11-CLI-A | Windows 11 | 192.168.10.10 | Client Workstation |
| DC01 | Windows Server 2025 | 192.168.10.20 | Domain Controller / DNS / DHCP |
| UBUNTU-SRV | Ubuntu Server | 192.168.10.30 | Remote Server |
| UBUNTU-DSK | Ubuntu Desktop | 192.168.10.40 | Linux Client Workstation |

---

## Technologies Used
* Windows Server 2025 (Active Directory, DNS, DHCP)
* Windows 11 & Ubuntu Linux (Server/Desktop)
* pfSense Firewall
* SSH & UTM Virtualization

---

## Troubleshooting Scenarios

### 1. Windows Client Performance Issue
Investigated a slow system by analyzing resource usage in Task Manager and reviewing logs in Event Viewer.

### 2. DNS Resolution Failure
* **Problem:** External websites wouldn't load (`nslookup google.com` timed out), but local network systems worked.
* **Root Cause:** The client automatically prioritized an unconfigured IPv6 link-local DNS address from the gateway.
* **Resolution:** Disabled IPv6 on the client network adapter, forcing traffic to use the internal AD DNS server (`192.168.10.20`).

### 3. DHCP Service Verification
Checked the DHCP service state on the Windows Server to ensure IP leases were being handed out properly to clients.

### 4. Remote Server Support via SSH
Established remote command-line access to the Ubuntu Server and verified that the SSH service was running securely.

### 5. Security and Final Validation
Verified firewall protection rules and confirmed network-wide functionality after all fixes were applied.

---

## Screenshots

### Lab Overview
![Lab Overview](screenshots/lab-overview.png)

### Windows Performance Troubleshooting
![Windows Performance Troubleshooting](screenshots/performance-troubleshooting.png)

### DNS Troubleshooting
![DNS Troubleshooting](screenshots/dns-troubleshooting.png)

### DHCP Verification
![DHCP Verification](screenshots/dhcp-verification.png)

### Remote Support
![Remote Support](screenshots/remote-support.png)

### Security and Final Validation
![Security and Final Validation](screenshots/security-validation.png)
