# Footprinting & Reconnaissance Attacks with GHDB (W2-PM2)

![Educational Purpose Only](https://shields.io)
![Technique](https://shields.io)
![Topic](https://shields.io)

## 📋 Project Overview
This repository contains the lab documentation, methodology, and findings for **Week 2 | Project Module 2 (W2-PM2)** from NetworkWalks. 

The **Google Hacking Database (GHDB)**, maintained by Exploit-DB, is a curated collection of specialized search queries known as **Google Dorks**. By combining advanced Google search operators, security researchers and penetration testers can passively uncover sensitive assets accidentally indexed by search engines—such as exposed webcams, open directory listings, configuration files, and public documents—without sending a single packet directly to the target.

---

## 🛠️ Tools & Resources Used
* **Search Engine:** Google Search (`google.com`)
* **Dork Repository:** [Exploit-DB Google Hacking Database (GHDB)](https://exploit-db.com)
* **Supplementary OSINT Platforms:** Shodan, Censys, Insecam, GitHub Dork Repositories

---

## 🚀 Lab Tasks & Findings

### Task 1: Discovering Exposed Live Security Cameras
**Objective:** Use GHDB dorks and OSINT techniques to locate **10x live, publicly accessible IP security cameras** exposed on the internet.

#### Methodology
1. Navigate to `://exploit-db.com` and select **GHDB** from the navigation menu.
2. Filter dorks using keywords like `"cam"` or `"webcam"`.
3. Execute the dorks on Google Search, verify live feeds, and log the findings.

#### Sample Dorks Used
```text
intitle:"webcamXP" inurl:8080
intitle:"Live View / - AXIS"
intitle:"EvoCam" inurl:"webcam.html"
inurl:indexFrame.shtml "Axis Video Server"
inurl:"MultiCameraFrame?Mode=Motion"
```

#### Results Log

| No. | Exposed Link | Relevant Dork | Username / Password (if any) |
| :--- | :--- | :--- | :--- |
| 1 | `http://122.116.41` *(Lab Example)* | `intitle:"webcamXP" inurl:8080` | `---` |
| 2 | *[Add your verified link]* | *[Add dork]* | *[Add credentials if applicable]* |
| 3 | *[Add your verified link]* | *[Add dork]* | *[Add credentials if applicable]* |
| 4 | *[Add your verified link]* | *[Add dork]* | *[Add credentials if applicable]* |
| 5 | *[Add your verified link]* | *[Add dork]* | *[Add credentials if applicable]* |
| 6 | *[Add your verified link]* | *[Add dork]* | *[Add credentials if applicable]* |
| 7 | *[Add your verified link]* | *[Add dork]* | *[Add credentials if applicable]* |
| 8 | *[Add your verified link]* | *[Add dork]* | *[Add credentials if applicable]* |
| 9 | *[Add your verified link]* | *[Add dork]* | *[Add credentials if applicable]* |
| 10 | *[Add your verified link]* | *[Add dork]* | *[Add credentials if applicable]* |

---

### Task 2: Locating Open Directories with Downloadable Mathematics PDFs
**Objective:** Use directory-listing dorks to locate **10x public open directories** containing downloadable Mathematics eBooks in `.pdf` format.

#### Sample Dorks Used
```text
intitle:index.of "parent directory" mathematics pdf
intitle:"index of" "mathematics" filetype:pdf
```

#### Results Log

| No. | Directory / Listing Link | Relevant Dork | Username / Password (if any) |
| :--- | :--- | :--- | :--- |
| 1 | `https://skylineuniversity.ac.ae` *(Lab Example)* | `intitle:index.of "parent directory" mathematics pdf` | `---` |
| 2 | *[Add your verified link]* | *[Add dork]* | `---` |
| 3 | *[Add your verified link]* | *[Add dork]* | `---` |
| 4 | *[Add your verified link]* | *[Add dork]* | `---` |
| 5 | *[Add your verified link]* | *[Add dork]* | `---` |
| 6 | *[Add your verified link]* | *[Add dork]* | `---` |
| 7 | *[Add your verified link]* | *[Add dork]* | `---` |
| 8 | *[Add your verified link]* | *[Add dork]* | `---` |
| 9 | *[Add your verified link]* | *[Add dork]* | `---` |
| 10 | *[Add your verified link]* | *[Add dork]* | `---` |

---

## 💡 Key Takeaways
* **Zero-Touch Reconnaissance:** Because queries are processed entirely against Google's cached index, the target servers are never directly contacted during the discovery phase.
* **Defensive Auditing:** Security teams use these exact same dorks to audit their own domains, identify accidental directory indexing (`Options -Indexes`), and restrict sensitive assets via `robots.txt`, authentication, and firewall rules.

---

## ⚠️ Legal & Ethical Disclaimer
> **For Educational Purposes Only.**  
> The techniques and resources documented in this repository are strictly for educational purposes and authorized security research. Do not attempt to log into, alter, or interact with unauthorized devices or networks. Always operate within legal boundaries and ethical guidelines.

---

## 📚 Credits
* Lab Material & Curriculum: [NetworkWalks](https://networkwalks.com)
