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
<img width="672" height="640" alt="Image" src="https://github.com/user-attachments/assets/9b9e42bb-2218-44f5-91c8-a53ebb509b61" />

### Windows Performance Troubleshooting
<img width="672" height="531" alt="Image" src="https://github.com/user-attachments/assets/e1a40618-9fbc-4319-ada1-2433866580c4" />
<img width="673" height="530" alt="Image" src="https://github.com/user-attachments/assets/52c0d46e-d4fa-4703-9cc8-4865b8d96d63" />


### DNS Troubleshooting
<br><img width="422" height="606" alt="Image" src="https://github.com/user-attachments/assets/0bd90e9b-b938-41b0-8ed4-211b052d11bf" /></br>

<br><img width="421" height="569" alt="Image" src="https://github.com/user-attachments/assets/2b84034e-a7ac-47b1-951e-3edec8c9f4a4" /></br>

<br><img width="420" height="600" alt="Image" src="https://github.com/user-attachments/assets/2b9830ba-51c1-4e7b-b716-1bea21fdc2e6" /></br>

### DHCP Verification
<img width="421" height="637" alt="Image" src="https://github.com/user-attachments/assets/0be3af55-1f51-4443-8d5d-f2b6e2da4988" />

### Remote Support
<img width="421" height="651" alt="Image" src="https://github.com/user-attachments/assets/7b8e8dab-032a-4c88-9cdc-2f48f0b283e1" />




### Security and Final Validation
<img width="417" height="644" alt="Image" src="https://github.com/user-attachments/assets/31e44c04-fd4e-46d6-accb-f1a2ee2f1f34" />

