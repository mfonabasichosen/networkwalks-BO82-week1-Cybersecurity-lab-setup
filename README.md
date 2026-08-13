<h1 align="center">🔐💻Cybersecurity Lab Environment Setup</h1>

---

<p align="center"><strong>Building an isolated virtual lab for penetration testing and ethical hacking practice</strong></p>

<div align="center">
  
**![Skill](https://img.shields.io/badge/Cybersecurity-red?logo=hackthebox&logocolor=white)**
**![Virtualbox](https://img.shields.io/badge/-Virtualbox_v7.2-blue?logo=virtualbox&logocolor=white)**
**![Kali](https://img.shields.io/badge/Kali_Linux_v2026.1-7C3AED?logo=kalilinux&logoColor=white)**
**![Network](https://img.shields.io/badge/Network-10.0.0.0%2F24-14b8a6)**
**![Pentest](https://img.shields.io/badge/Penetration_Testing-red?logo=kalilinux&logoColor=black)**
**![Skill](https://img.shields.io/badge/Virtualization-blue?logo=virtualbox&logocolor=white)**
**![Tool](https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white)**
**![NetworkWalks](https://img.shields.io/badge/NetworkWalks-b22222)**
**![Hacking](https://img.shields.io/badge/Ethical_Hacking-green?logo=kalilinux&logoColor=black)**
**![Skill](https://img.shields.io/badge/Skill-Linux-red?logo=linux&logoColor=blue)**
**![Chosen Mfonabasi](https://img.shields.io/badge/Chosen_Mfonabasi-red?logo=github&logocolor=white)**

**VirtualBox • Kali Linux • Virtual Networking • Linux Networking**

</div>

## 📌 Project Overview

This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

---

## 🎯 Objectives

The main objectives of this project are to:

- Install and configure VirtualBox.
- Install/import Kali Linux as a virtual machine.
- Create a private **NAT Network** for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent IP address to the Kali VM.
- Verify network connectivity and DNS resolution.
- Take a clean VM snapshot for recovery.
- Document the complete setup process.
- Prepare the environment for future cybersecurity projects.

---

## 🛡️ Purpose of the Lab
The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

⚠️ **Important:** This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

---

## 🏗️ Lab Architecture
The setup consists of my Host OS running Ubuntu Linux distro. Inside Ubuntu, VirtualBox hosts one virtual machines — Kali Linux — connected through a NAT Network for isolated cybersecurity practice.

<img width="1920" height="1079" alt="1-Screenshot-VB-environment" src="https://github.com/user-attachments/assets/bb91501f-b97c-41e3-b9fe-9492135c85de" />


Additional target machines can be added to the same virtual machine in future projects.

---

## ⚙️ Lab Configuration

| 🧩 Component | ⚙️ Configuration |
|---|---|
| 🖥️ Host OS | Ubuntu 24.04 |
| 🧠 Host RAM | 8 GB |
| ⚡ Processor | Intel Core i7 |
| 📦 Hypervisor | VirtualBox 7.2 |
| 🐉 Security OS | Kali Linux 2026.1 |
| 🧠 Kali RAM | 2048 MB |
| 🌐 Virtual Network | NAT Network |
| 🛰️ Network Address | 10.0.0.0/24 |
| 🐾 Kali IP Address | 10.0.0.2/24 |
| 🚪 Default Gateway | 10.0.0.1 |
| 🌍 DNS Server | 8.8.8.8 |
| 🪐 Future VM Range | 10.0.0.3–10.0.0.99 |

---

## 🎞️ Lab Setup Procedure

### Step 1. Install VirtualBox

VirtualBox was installed as the hypervisor.

---

### Step 2. Create the NAT Network

A dedicated NAT Network was created in VirtualBox.

Configuration: Network Name: NatNetwork IPv4 Prefix: 10.0.0.0/24 DHCP: Enabled IPv6: Disabled
<img width="1920" height="1069" alt="2-Screenshot-VB-network-settings" src="https://github.com/user-attachments/assets/86c7c671-8686-4727-aac6-2920638c1422" />


A **NAT Network** was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

---

### Step 4. Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

```
Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
```

The VM was allocated:

```
RAM: 2048 MB
```
<img width="1920" height="1080" alt="3-Screenshot-kali-linux" src="https://github.com/user-attachments/assets/ba1cc17d-96b0-4678-b8ea-53cec53e6986" />


A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

---

### Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.
<img width="1920" height="1080" alt="4-Screenshot-kali-network-settings" src="https://github.com/user-attachments/assets/ed37bbdf-fdcd-4212-aff1-aa161ec72eb8" />

---

### Step 6. Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

```
Clean Kali - Network Setup
```

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

---

## 🔍 Lab Verification

| ✅ Test | 📋 Command | 🎯 Expected Result |
|---|---|---|
| 🌐 Check IP address | `ip a` | Correct Kali IP displayed |
| 📡 Test gateway | `ping 10.0.0.1` | Successful replies |
| 🌍 Test Internet connectivity | `ping 8.8.8.8` | Successful replies |
| 🔍 Test DNS resolution | `nslookup networkwalks.com` | Domain resolves |
| 🛡️ Verify Nmap | `nmap --version` | Nmap version displayed |
| 📸 Verify snapshot | Restore snapshot and run `ip a` | Baseline configuration restored |

### Example Results

```
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8
```
---

### 🐞 Problems Encountered & Solutions

Documenting problems is an important part of the project.

### Problem 1. Internet Connectivity After Static IP Configuration

After manually configuring the IPv4 settings, Internet connectivity may fail depending on the Kali/NetworkManager configuration.

One workaround used during this lab was:

```
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

The network connection was then restarted/rebooted and connectivity was tested again.

> **Important:** Network interface and connection names may differ between systems. Students should first identify their actual connection name before running an `nmcli` command.

### Problem 2 — DNS Not Working in Kali Linux VM

**Problem:** After configuring the network, my Kali VM had no working internet access through domain names. The IP address was working but DNS resolution was failing.

**Error:**

```
ping: google.com: Temporary failure in name resolution
```

**What I noticed:** Pinging 8.8.8.8 directly worked fine, which meant my internet connection was active. However, pinging google.com failed because DNS was not resolving domain names to IP addresses.

**Solution:** I manually configured the DNS servers using nmcli:

```
sudo nmcli connection modify "Wired connection 1" ipv4.dns "1.1.1.1 8.8.8.8" ipv4.ignore-auto-dns yes
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

**Verification:**

```
ping -c 4 google.com
```

**Result:**

```
64 bytes from google.com: icmp_seq=1 ttl=118
4 packets transmitted, 4 received, 0% packet loss
```

After setting the DNS servers manually to 1.1.1.1 and 8.8.8.8, domain name resolution started working correctly.

---

**💡 What I Learned**

Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

### 1. NAT vs NAT Network

A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

### 2. Virtual Machine Networking

I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

### 3. Static IP Configuration

I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

### 4. VM Snapshots

I learned that a clean snapshot should be created **before performing risky or experimental activities**.

This provides a known-good recovery point for future cybersecurity exercises.

### 5. Documentation

I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

---

## 🔐 Security & Ethical Use

This laboratory is intended strictly for education purposes only.

---

## 🔗 Tools & Resources

- **VirtualBox:** https://virtualbox.org/wiki/Downloads
- **Kali Linux:** https://kali.org/get-kali

---
## 👤 Author

**Chosen Mfonabasi**  
Cybersecurity Intern(Networkwalks Academy- Batch B082)

LinkedIn: www.linkedin.com/in/chosen-mfonabasi-5a297a3b7

---

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup | **Repository:** GitHub
