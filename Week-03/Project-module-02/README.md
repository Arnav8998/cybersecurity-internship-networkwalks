# Password Cracking with NetworkWalks Tools (W3-PM2)

![Educational Purpose Only](https://shields.io)
![Platform](https://shields.io)
![Technique](https://shields.io)

## 📋 Project Overview
This repository contains the lab documentation, workflow, and password recovery results for **Week 3 | Project Module 2 (W3-PM2)** from NetworkWalks.

**Password cracking** demonstrates how weak or predictable passwords protecting documents (such as PDF, ZIP, and Office files) can be recovered by extracting their cryptographic hash digest and testing candidate words against it. Unlike traditional local CLI utilities, this module utilizes browser-based tools provided by NetworkWalks to extract a PDF hash locally in the browser and execute a dictionary attack without requiring local software installation.

---

## 🛠️ Tools & Prerequisites
* **Operating System:** Windows or Kali Linux (any modern web browser)
* **Hash Extractor:** [NetworkWalks Hash Calculator](https://networkwalks.com)
* **Cracking Engine:** [NetworkWalks Password Cracker](https://networkwalks.com)
* **Target File:** `My Locked PDF1.pdf` (from the [W3-PM2 Lab Page](https://networkwalks.com))

---

## 🚀 Lab Execution & Walkthrough

### Step 1: Extract the PDF Hash
1. Download the encrypted target file (`My Locked PDF1.pdf`) to your machine.
2. Open the [NetworkWalks Hash Calculator](https://networkwalks.com) in your browser and select the **PDF** tab.
3. Upload `My Locked PDF1.pdf`. The tool parses the file locally in your browser and outputs a `pdf2john` / `hashcat`-compatible hash string starting with `$pdf$...`.
4. Click **Copy** to copy the complete hash value.

---

### Step 2: Execute a Dictionary Attack
1. Open the [NetworkWalks Password Cracker](https://networkwalks.com) in your browser.
2. Paste the full `$pdf$...` hash into the **PDF HASH** input field.
3. Select a wordlist (using the default **Built-in list (100 passwords)** or uploading a custom `.txt` wordlist) and click **START CRACKING**.
4. Wait for the dictionary attack to match the hash digest and display the plaintext password.

---

### Step 3: Unlock the PDF & Capture the Flag
1. Open `My Locked PDF1.pdf` in a PDF reader.
2. Enter the recovered password when prompted to decrypt the document and view the completion flag.

#### Key Findings
* **Attack Method:** Dictionary Attack (matched at attempt `81 / 100`)
* **Recovered Password:** `password1`
* **Result:** Successfully decrypted `My Locked PDF1.pdf` and captured the 1st flag.

---

## 💡 Key Takeaways
* **Encryption vs. Hashing:** Encryption is a two-way reversible function requiring a key to restore plaintext, whereas hashing is a one-way mathematical function that generates a fixed-length message digest.
* **Password Entropy & Length:** Short or common dictionary words (like `password1` or `123456`) are cracked in seconds, whereas long (12+ character) high-entropy passphrases dramatically increase cracking time.

---

## ⚠️ Legal & Ethical Disclaimer
> **For Educational Purposes Only.**  
> The tools and techniques documented in this project are intended strictly for educational use and authorized security testing. Only audit files, systems, or networks you own or have explicit written permission to test.

---

## 📚 Credits
* Lab Material & Tools: [NetworkWalks](https://networkwalks.com)
