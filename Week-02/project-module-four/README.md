# Footprinting & Reconnaissance with theHarvester (W2-PM4)

![Educational Purpose Only](https://shields.io)
![Platform](https://shields.io)
![Tool](https://shields.io)

## 📋 Project Overview
This repository contains the lab documentation, commands, and OSINT findings for **Week 2 | Project Module 4 (W2-PM4)** from NetworkWalks.

**theHarvester** is a Python-based Open-Source Intelligence (OSINT) and footprinting tool created by Christian Martorella (Edge-Security Research). It passively gathers email addresses, subdomains, hostnames, employee names, open ports, and service banners from public sources such as search engines, PGP key servers, and Shodan without directly touching the target infrastructure.

---

## 🛠️ Tools & Installation
* **Operating System:** Kali Linux (pre-installed)
* **Target Domain:** `microsoft.com`
* **Tool Version:** `theHarvester 4.10.1`

### Alternative Installation (Non-Kali Debian/Ubuntu Systems)
If `theHarvester` is not pre-installed on your system, install it via APT or clone the official repository:
```bash
# Option 1: Package Manager
sudo apt-get install theHarvester

# Option 2: GitHub Repository
git clone https://github.com
cd theHarvester
sudo python ./theHarvester.py
```


---

## 🚀 Lab Tasks & Execution

### Command Flags Reference
* `-d` : Target domain to search
* `-l` : Limit the number of search results
* `-b` : Data source (e.g., `baidu`, `crtsh`, `duckduckgo`, `yahoo`, `all`)

---

### Task 1: Targeted Search Using Baidu (`-b baidu`)
**Objective:** Gather email IDs and subdomains associated with `microsoft.com` using Baidu as the data source, capped at 1,000 results.

```bash
theHarvester -d microsoft.com -l 1000 -b baidu
```


* **Key Findings:** Harvested public email addresses (e.g., `viva-noreply@microsoft.com`) directly from indexed search results without triggering target alerts. *(Note: Exact counts vary over time as search engine indexing algorithms update).*

---

### Task 2: Comprehensive Search Across All Sources (`-b all`)
**Objective:** Gather email IDs and subdomains associated with `microsoft.com` across all supported public data sources, limited to 50 results per source.

```bash
theHarvester -d microsoft.com -l 50 -b all
```


* **Key Findings:** Aggregates intelligence across dozens of passive engines simultaneously (`crtsh`, `dnsdumpster`, `hackertarget`, `rapiddns`, `urlscan`, `waybackarchive`, etc.) to uncover hidden subdomains and organizational contact points. *(Sources requiring third-party API keys in `api-keys.yaml` will display a missing-key notice unless configured).*

---

## 💡 Key Takeaways
* **Stealthy Passive Recon:** `theHarvester` queries third-party aggregators and search engines rather than scanning the target directly, making detection nearly impossible.
* **Attack Surface Mapping:** Harvested emails provide targets for social engineering or credential-stuffing analysis, while discovered subdomains reveal forgotten or unpatched entry points.
* **Defensive Hygiene:** Security teams run `theHarvester` against their own domains to identify and minimize public metadata leaks.

---

## ⚠️ Legal & Ethical Disclaimer
> **For Educational Purposes Only.**  
> The tools and techniques documented in this project are intended strictly for educational use and authorized security testing. Only perform reconnaissance on networks or domains you own or have explicit written permission to test. Unauthorized access or misuse is illegal.

---

## 📚 Credits
* Lab Material & Curriculum: [NetworkWalks](https://networkwalks.com)
