# Footprinting with Maltego (W2-PM3)

![Educational Purpose Only](https://shields.io)
![Tool](https://shields.io)
![Topic](https://shields.io)

## 📋 Project Overview
This repository contains the lab setup, walkthrough, and OSINT findings for **Week 2 | Project Module 3 (W2-PM3)** from NetworkWalks.

**Maltego** is an open-source intelligence (OSINT) and graphical link analysis tool originally created by Paterva in 2008. It enables security analysts and penetration testers to visually map relationships between domains, infrastructure, email addresses, people, and organizations using automated queries called **Transforms**.

In this module, Maltego is installed on Windows and used to harvest public email addresses associated with the target domain `networkwalks.com`.

---

## 🛠️ Tools & Prerequisites
* **Operating System:** Windows (also compatible with Kali Linux)
* **Software:** Maltego Graph Desktop (v4.11.3 / Community Edition) + Eclipse Temurin JRE 17 (x64)
* **Account:** Free Maltego ID
* **Target Domain:** `networkwalks.com` (authorized target)

---

## 🚀 Lab Tasks & Execution

### Task 1: Download, Install & Configure Maltego
1. **Download:** Visit [maltego.com](https://maltego.com) and download the **Maltego Graph for Windows (+ Java x64)** installer.
2. **Install Prerequisites & Application:** Run the setup executable (`MaltegoSetup.JRE64.v4.11.3.exe`). Follow the wizard to install Eclipse Temurin JRE 17 and the Maltego Desktop client.
3. **Activate via Maltego ID:** Launch Maltego (Run as administrator), select **Maltego ID** under Activation Options, and accept the End User License Agreement.
4. **Authenticate:** Click **Browser Login**, register a free Maltego ID account, and complete browser authentication.
5. **Finalize Setup:** Keep default transform sources (`Utilities`), browser settings, and `Normal` privacy mode to reach the main investigation canvas.

---

### Task 2: Harvesting Domain Email Addresses (`networkwalks.com`)
1. **Create a Graph:** Open a new graph (`Ctrl + T` or click the **New Graph** icon).
2. **Add Domain Entity:** In the **Entity Palette**, search for `"Domain"` and drag the **Domain** entity onto the main workspace.
3. **Set Target:** Double-click the entity and rename it from the default (`maltego.com`) to `networkwalks.com`.
4. **Run Email Transforms:** Right-click the `networkwalks.com` entity, filter the **Run Transforms** menu for `"email"`, and execute the email discovery transforms (such as *To Email Addresses [Search Engine]* and *To Email Address [From whois info]*).

#### Key Findings
* **Discovered Email Address:** `info@networkwalks.com`
* **Additional Available Transforms:** Beyond email harvesting, Maltego can map DNS records, domain owner WHOIS details, historical snapshots, and associated personnel.

---

## 💡 Key Takeaways
* **Visual Link Analysis:** Maltego transforms raw OSINT data into visual node graphs, making complex infrastructure and personnel connections easy to trace and export (PDF, XLSX, CSV, or images).
* **Attacker vs. Defender Perspective:** Attackers use harvested emails and tech stacks to craft targeted phishing campaigns or look up software-specific exploits. Defenders run these transforms on their own domains to audit public exposure.

---

## ⚠️ Legal & Ethical Disclaimer
> **For Educational Purposes Only.**  
> The tools and techniques documented in this project are intended strictly for educational use and authorized security testing. Only perform reconnaissance on systems you own or have explicit written permission to test. Unauthorized testing or misuse is illegal.

---

## 📚 Credits
* Lab Material & Curriculum: [NetworkWalks](https://networkwalks.com)
