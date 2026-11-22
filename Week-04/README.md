# Black-Box Penetration Testing Project: Mediroza General Hospital (Week 4)

![Educational Purpose Only](https://shields.io)
![Engagement Type](https://shields.io)
![Duration](https://shields.io)
![Batch](https://shields.io)

## 📋 Engagement Overview
This repository documents the full **Black-Box Penetration Testing & Vulnerability Assessment** conducted for **Mediroza General Hospital** (`https://medirozahospital.com`) as part of the **NetworkWalks Cybersecurity & Ethical Hacking Capstone (Batch B083 | Week 4)**.

The objective of this 5-day engagement is to simulate an external attacker with no prior internal knowledge, identify security weaknesses across the client's web infrastructure, demonstrate real-world business impact across four structured milestones, and deliver an actionable remediation report.

---

## 🎯 Scope & Rules of Engagement (RoE)
* **Client:** Mediroza General Hospital
* **Target Domain:** `https://medirozahospital.com`
* **Assessment Type:** Full Black-Box Penetration Test
* **Authorization:** Explicit written permission granted by the client (controlled lab environment)
* **Timeline:** 5 Days (Independent execution)
* **Strict Boundaries:**
  * Testing is strictly restricted to `https://medirozahospital.com`.
  * **No** social engineering attacks.
  * **No** Denial-of-Service (DoS / DDoS) testing.
  * **No** testing outside the agreed scope.

---

## 🗺️ Project Milestones & Deliverables

### Milestone 1 (M1): Initial Access & File Retrieval
* **Objective:** Attack the target web application and retrieve **3 confidential patient PDF lab reports**.
* **Methodology:**
  * Perform passive and active reconnaissance on `medirozahospital.com`.
  * Enumerate exposed endpoints, directories, and authentication portals.
  * Analyze input handling and authentication mechanisms to bypass restrictions and gain unauthorized access.
* **Deliverable:** Proof of unauthorized access and the 3 retrieved encrypted PDF lab reports.

---

### Milestone 2 (M2): Data Extraction & Decryption
* **Objective:** Crack the encryption protecting all **3 retrieved patient PDF files**.
* **Methodology:**
  * Inspect encryption algorithms and extract hashes (`pdf2john` / hash extractors) for each file.
  * Apply tailored cracking strategies and wordlists (recognizing that each file may require a distinct approach or wordlist).
* **Deliverable:** Decrypted contents of all 3 patient lab reports with proof of access.

---

### Milestone 3 (M3): Critical Server Data Exposure
* **Objective:** Pivot from initial findings to uncover critical internal hospital records exposed on the server.
* **Specific Targets:**
  1. Complete **staff salary records** for hospital employees.
  2. **Shareholder details** of Mediroza General Hospital.
* **Methodology:**
  * Thoroughly inspect all previously recovered files, metadata, and file properties for hidden clues or server paths.
  * Leverage discovered pointers to locate and document the critical server data exposure.
* **Deliverable:** Full documented evidence of the exposure and a structured summary of the uncovered confidential data.

---

### Milestone 4 (M4): Professional Penetration Testing Report
* **Objective:** Compile all technical findings, evidence, risk ratings, and remediation guidance into a formal client-ready deliverable.
* **Required Report Structure:**
  1. **Executive Summary:** High-level overview of the engagement, critical findings, and business/compliance impact.
  2. **Scope & Methodology:** Target boundaries, tools utilized, testing approach, and limitations.
  3. **Findings & Proof of Exploitation:** Step-by-step technical walkthroughs, commands, and screenshots for Milestones 1–3.
  4. **Risk Rating:** Severity classification (`Critical`, `High`, `Medium`, `Low`) with clear justification for each vulnerability.
  5. **Recommendations & Remediation:** Practical, prioritized engineering steps to patch each flaw.

---

## 📁 Suggested Repository Structure
```text
├── README.md
├── M1-Initial-Access/
│   ├── recon-notes.md
│   └── screenshots/
├── M2-Data-Extraction/
│   ├── cracking-notes.md
│   └── screenshots/
├── M3-Critical-Exposure/
│   ├── exposure-summary.md
│   └── screenshots/
└── M4-Final-Report/
    └── Mediroza_Hospital_Pentest_Report.pdf
```

---

## ⚠️ Legal & Ethical Disclaimer
> **For Educational Purposes Only.**  
> This project is conducted strictly within a controlled, authorized environment provided by NetworkWalks. Never apply offensive security techniques, exploitation, or unauthorized data access against any system without explicit written permission from the system owner.

---

## 📚 Credits
* Project Scenario & Curriculum: [NetworkWalks](https://networkwalks.com)
