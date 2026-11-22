# Network Scanning with Zenmap (W2-PM5)

![Educational Purpose Only](https://shields.io)
![Platform](https://shields.io)
![Tool](https://shields.io)

## 📋 Project Overview
This repository contains the lab documentation, scan commands, and network discovery findings for **Week 2 | Project Module 5 (W2-PM5)** from NetworkWalks.

**Zenmap** is the official cross-platform graphical user interface (GUI) for **Nmap** (Network Mapper). It allows security analysts and network administrators to perform host discovery, port scanning, OS fingerprinting, and visual network topology mapping using pre-configured or custom scan profiles.

In this lab, Zenmap is installed on Windows to perform a Ping Scan (`nmap -sn`) across a local area network (LAN) subnet, identify active hosts and MAC addresses, and export a visual network topology map.

---

## 🛠️ Tools & Prerequisites
* **Operating System:** Windows PC
* **Software:** Nmap & Zenmap GUI (`nmap-7.91-setup.exe` or latest stable release from [nmap.org](https://nmap.org))
* **Target Network:** Local LAN Subnet (Lab reference subnet: `10.0.0.0/24`)

---

## 🚀 Lab Tasks & Execution

### Task 1: Download & Install Zenmap
1. Visit the official Nmap download page at `https://nmap.org` and download the latest Windows binary installer.
2. Run the setup executable and accept the license agreement.
3. Ensure **Zenmap (GUI Frontend)** and **Npcap** are selected in the component list, then complete the installation.

---

### Task 2: Identify Local IP Address & LAN Subnet
Open Windows Command Prompt (`cmd`) and run `ipconfig` to determine the host's IPv4 address and subnet mask:
```cmd
ipconfig
```
* **Lab Reference Host IP:** `10.0.0.5`
* **Subnet Mask:** `255.255.255.0` (`/24`)
* **Target Network Range:** `10.0.0.0/24`

---

### Task 3: Discover Live Hosts via Ping Scan
1. Launch **Zenmap**.
2. Enter the target subnet (`10.0.0.0/24`) into the **Target** field.
3. Select **Ping scan** from the **Profile** dropdown and click **Scan**.

**Underlying Nmap Command Executed:**
```bash
nmap -sn 10.0.0.0/24
```

---

### Tasks 4, 5 & 6: Host Discovery Summary
*(Note: To retrieve the local machine's own MAC address on Windows, run `ipconfig /all` in Command Prompt).*

* **Total Live Hosts (Task 4):** `4` active hosts (including the scanning PC)
* **Discovered IPs & MAC Addresses (Tasks 5 & 6):**

| Host # | IP Address | MAC Address | Vendor / Notes |
| :--- | :--- | :--- | :--- |
| 1 | `10.0.0.1` | `00:50:56:E3:B3:2C` | VMware |
| 2 | `10.0.0.4` | `00:0C:29:C0:94:8F` | VMware |
| 3 | `10.0.0.19` | `00:50:56:E9:64:82` | VMware |
| 4 | `10.0.0.5` | `00-0C-29-40-C0-93` | Local Scanning PC (`ipconfig /all`) |

---

### Task 7: Generate & Export Network Topology Map
1. Navigate to the **Topology** tab in Zenmap after the scan completes.
2. Click **Legend** to review host color codes, traceroute connection styles, and device icons.
3. Click **Save Graphic**, choose **PDF** as the file format, and export the topology diagram (`Zenmap1.pdf`) to the Desktop for reporting.

---

## 💡 Key Takeaways
* **Host Discovery (`-sn`):** A Ping Scan disables port scanning and focuses solely on determining which IP addresses are online via ICMP/ARP requests, making initial network mapping fast and lightweight.
* **Visual Topology:** Zenmap's topology view helps defenders visualize network segmentation, gateways, and active endpoints at a glance.

---

## ⚠️ Legal & Ethical Disclaimer
> **For Educational Purposes Only.**  
> The tools and techniques documented in this project are intended strictly for educational use and authorized network auditing. Only scan networks you own or have explicit written permission to test. Unauthorized network scanning may violate organizational policies or local laws.

---

## 📚 Credits
* Lab Material & Curriculum: [NetworkWalks](https://networkwalks.com)
* Practice Lab Questions: [NetworkWalks Zenmap Practice Lab](https://networkwalks.com)
