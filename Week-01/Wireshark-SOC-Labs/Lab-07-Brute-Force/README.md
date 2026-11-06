## Investigation Results

**Status:** Investigation findings documented – completion evidence pending

**Final Score:** Pending verification

### Key Findings

The investigation examined suspicious FTP authentication traffic directed towards an internal FTP server (`192.168.10.20`). The objective was to identify the source of repeated failed login attempts, determine whether an attacker successfully authenticated and classify the attack.

Analysis of the supplied network capture identified **369 packets**. Using Wireshark's **Statistics → Protocol Hierarchy** feature and the `ftp` display filter, the investigation identified FTP authentication traffic containing repeated `USER` and `PASS` commands.

Applying the display filter `ftp.request.command == "PASS"` identified `192.168.10.66` as the source of the password attempts. Further examination using `ftp.request.command == "USER"` established that the attacker repeatedly targeted the `admin` account.

Filtering FTP responses with `ftp.response.code == 530` identified **24 failed authentication attempts**, each returning the response `530 Login incorrect`.

However, applying `ftp.response.code == 230` revealed one successful authentication response. Using **Follow TCP Stream**, the investigation identified the simulated password `Sunshine99` immediately before the successful login response.

These findings demonstrate a successful FTP password brute-force attack in which repeated authentication attempts eventually resulted in access to the targeted account.

### Investigation Summary

| Investigation Item | Result |
|---|---|
| Packets captured | 369 |
| Attacker IP | `192.168.10.66` |
| Target FTP server IP | `192.168.10.20` |
| Application protocol | FTP |
| Targeted username | `admin` |
| Failed login attempts | 24 |
| Failed authentication response | `530 Login incorrect` |
| Successful login responses | 1 |
| Successful authentication response | `230 Login successful` |
| Successful password | `Sunshine99` (simulated) |
| Investigation technique | FTP filtering and Follow TCP Stream |
| Attack classification | FTP password brute-force attack |

### Security Classification

**Successful FTP Password Brute-Force Attack**

The investigation identified repeated authentication attempts originating from a single IP address against the same FTP account.

The sequence of 24 failed logins followed by one successful authentication response is consistent with a password brute-force attack.

The FTP server's `230 Login successful` response confirms that authentication succeeded within the simulated environment. However, the available evidence does not establish whether the attacker subsequently accessed, modified or transferred files.

The investigation also demonstrates the risks associated with traditional FTP, which can transmit authentication credentials without transport encryption.

### Security Implications

Successful brute-force attacks can result in unauthorised access to organisational systems, potentially exposing sensitive files, administrative accounts and connected infrastructure.

The repeated authentication failures indicate that the FTP server permitted multiple unsuccessful login attempts before accepting a valid password.

Organisations should implement authentication rate limiting, account lockout or progressive delays, strong password policies and centralised monitoring of failed authentication attempts.

Where possible, legacy FTP services should be replaced with secure alternatives such as SFTP or FTPS to protect credentials and transferred information.

Additional measures, including IP-based access restrictions, intrusion detection and alerting for repeated failed logins, can help identify and reduce automated password attacks.

Following a confirmed unauthorised login, security teams should investigate subsequent account activity, review file access logs, reset affected credentials and assess whether further compromise occurred.

### Evidence

- Wireshark packet capture showing 369 packets – pending screenshot
- FTP protocol identification – pending screenshot
- FTP `USER` and `PASS` commands – pending screenshot
- Display filter `ftp.response.code == 530` showing 24 failed attempts – pending screenshot
- Display filter `ftp.response.code == 230` showing successful authentication – pending screenshot
- Follow TCP Stream showing the successful authentication sequence – pending screenshot (password redacted)
- Official Networkwalks completion result – pending upload

### Skills Demonstrated

- Network Traffic Analysis
- FTP Protocol Investigation
- Wireshark Display Filtering
- Authentication Failure Analysis
- FTP Response Code Interpretation
- TCP Stream Reconstruction
- Brute-Force Attack Detection
- Security Incident Investigation
- SOC Investigation Reporting
