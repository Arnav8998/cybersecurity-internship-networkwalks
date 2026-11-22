# Footprinting & Reconnaissance Attacks with Multiple Kali Tools (W2-PM1)

![Educational Purpose Only](https://shields.io)
![Platform](https://shields.io)
![Topic](https://shields.io)

## 📋 Project Overview
This repository contains the lab documentation, commands, and findings for **Week 2 | Project Module 1 (W2-PM1)** from NetworkWalks. 

**Reconnaissance (Footprinting)** is the foundational phase of ethical hacking and penetration testing. Before interacting directly with a target, security professionals passively gather publicly available information to build a complete profile of the target's infrastructure, technologies, and defensive posture without triggering alerts.

In this lab, six built-in Kali Linux reconnaissance tools are used to footprint the target domain `networkwalks.com`.

---

## 🛠️ Tools & Prerequisites
* **Operating System:** Kali Linux
* **Target Domain:** `networkwalks.com`
* **Tools Used:** `whois`, `whatweb`, `nslookup`, `curl`, `wafw00f`, `dnsrecon`

---

## 🚀 Lab Tasks & Execution

### Task 1: Domain Registration Lookup (`whois`)
Query the public domain registration record to identify ownership details, registration/expiry dates, and authoritative name servers.
```bash
whois networkwalks.com
```
* **Key Findings:** Reveals the registrar (GoDaddy) and name servers pointing to **HostGator**, identifying the underlying hosting provider.

---

### Task 2: Web Technology Fingerprinting (`whatweb`)
Identify the web server, content management system (CMS), plugins, frameworks, and IP address running on the target.
```bash
whatweb networkwalks.com
```
* **Key Findings:** Exposes the server IP (`192.232.216.135`), Apache web server, **WordPress 7.0.4**, and plugins such as **WP Download Manager 3.3.58**, which can be cross-referenced against vulnerability databases.

---

### Task 3: DNS IP Resolution (`nslookup`)
Resolve the target domain name into its corresponding IPv4 address.
```bash
nslookup networkwalks.com
```
* **Key Findings:** Resolves `networkwalks.com` to `192.232.216.135`, allowing direct server mapping and reverse-IP lookups.

---

### Task 4: HTTP Response Header Inspection (`curl`)
Read the raw HTTP response headers to inspect server banners, caching layers, cookies, and exposed endpoints.
```bash
curl -I https://networkwalks.com
```
* **Key Findings:** Reveals the Apache server banner, caching configuration (`x-nginx-cache`), and the WordPress REST API endpoint (`/wp-json/`).

---

### Task 5: Web Application Firewall Detection (`wafw00f`)
Detect whether a Web Application Firewall (WAF) is actively filtering traffic to the target site.
```bash
wafw00f networkwalks.com
```
* **Key Findings:** Confirms the site is protected behind **ModSecurity (SpiderLabs) WAF**, indicating that automated or noisy payloads may be blocked or logged.

---

### Task 6: Comprehensive DNS Enumeration (`dnsrecon`)
Enumerate all available DNS records, including Name Servers (NS), Mail Exchange (MX), Sender Policy Framework (SPF), TXT, and Service (SRV) records.
```bash
dnsrecon -d networkwalks.com
```
* **Key Findings:** Maps the mail server (`://networkwalks.com`), DNS software version (**Bind 9.16.23**), SPF policies, and cPanel autodiscovery service records.

---

## 💡 Key Takeaways
* **Passive Recon is Stealthy:** None of these tools actively exploit the target; they strictly query publicly exposed data.
* **Attack Surface Reduction:** The more metadata an organization exposes via headers, DNS, and registration records, the easier subsequent attack phases become. Defenders run these exact tools to audit and minimize their own public footprint.

---

## ⚠️ Legal & Ethical Disclaimer
> **For Educational Purposes Only.**  
> The techniques and tools documented in this project are intended strictly for educational use and authorized security testing. Unauthorized scanning, testing, or accessing of systems you do not own or lack explicit written permission to test is illegal. Always adhere to local laws and ethical guidelines.

---

## 📚 Credits
* Lab Material & Curriculum: [NetworkWalks](https://networkwalks.com)
