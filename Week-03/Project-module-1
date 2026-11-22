# Password Cracking with John the Ripper & Johnny (W3-PM1)

![Educational Purpose Only](https://shields.io)
![Platform](https://shields.io)
![Tool](https://shields.io)

## 📋 Project Overview
This repository contains the lab setup, walkthrough, and recovery results for **Week 3 | Project Module 1 (W3-PM1)** from NetworkWalks.

**John the Ripper (JTR)** is an open-source password security auditing and recovery tool capable of cracking numerous hash formats as well as password-protected archives and documents (PDF, ZIP, Office files). **Johnny** serves as the official cross-platform GUI frontend for JTR, allowing analysts to load hash files, launch attacks, and monitor cracking progress visually.

In this lab, JTR and Johnny are configured on Windows to extract the hash from an encrypted PDF (`My Locked PDF1.pdf`), crack the password, and capture the flag inside.

---

## 🛠️ Tools & Prerequisites
* **Operating System:** Windows PC *(Note: JTR comes pre-installed on Kali Linux)*
* **CLI Engine:** John the Ripper (`john-1.9.0-jumbo-1-win64`) from [Openwall](https://openwall.com)
* **GUI Frontend:** Johnny (`johnny 2.2 win64`) from [Openwall Johnny Wiki](https://openwall.info)
* **Hash Extraction Utility:** OnlineHashCrack PDF Hash Extractor (or `pdf2john.pl` included in JTR's `/run` folder)
* **Target File:** `My Locked PDF1.pdf`

---

## 🚀 Lab Execution & Walkthrough

### Step 1: Download & Configure JTR and Johnny
1. Download the **John the Ripper** Windows 64-bit binary archive (`1.9.0-jumbo-1`) and extract it.
2. Download and run the **Johnny GUI** Windows installer (`johnnyInstaller.exe`).
3. Launch **Johnny**, navigate to **Settings**, and click **Browse** next to *John the Ripper executable*.
4. Locate and select `john.exe` inside the extracted JTR directory (`.../john-1.9.0-jumbo-1-win64/run/john.exe`).

---

### Step 2: Extract the PDF Password Hash
1. Upload the encrypted target file (`My Locked PDF1.pdf`) to the [OnlineHashCrack PDF Hash Extractor](https://onlinehashcrack.com) (or run `perl pdf2john.pl "My Locked PDF1.pdf" > hash1.txt` locally).
2. Copy the generated hash string starting with `$pdf$...`.
   > **Important:** Ensure there are no leading/trailing wrapper characters (such as `b'`) before saving.
3. Paste the clean hash into Notepad and save it as `hash1.txt`.

---

### Step 3: Crack the Hash & Capture the Flag
1. Return to **Johnny** and click **Open password file**.
2. Select `hash1.txt` and click **Open**.
3. Click **Start new attack** to begin the password recovery process.
4. Once cracked, copy the plaintext password displayed in the **Password** column and open `My Locked PDF1.pdf`.

#### Key Findings
* **Recovered Password:** `password1`
* **Flag Status:** Unlocked `My Locked PDF1.pdf` and captured the 1st lab flag.

---

## 💡 Key Takeaways
* **Encryption vs. Hashing:** Encryption is a two-way reversible process requiring a key to decrypt data, whereas hashing is a one-way mathematical function producing a fixed-length digest. Password crackers work by hashing candidate words and comparing them against the extracted digest.
* **Password Complexity Matters:** Simple dictionary passwords like `password1` are cracked almost instantaneously by modern auditing tools, underscoring the importance of long, high-entropy passphrases.

---

## ⚠️ Legal & Ethical Disclaimer
> **For Educational Purposes Only.**  
> The tools and techniques documented in this project are intended strictly for educational use and authorized password auditing. Only test files, systems, or networks you own or have explicit written permission to audit. Unauthorized access is illegal.

---

## 📚 Credits
* Lab Material & Curriculum: [NetworkWalks](https://networkwalks.com)
