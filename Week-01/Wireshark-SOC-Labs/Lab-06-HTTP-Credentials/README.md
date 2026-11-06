## Investigation Results

**Status:** Investigation findings documented – completion evidence pending

**Final Score:** Pending verification

### Key Findings

The investigation examined unencrypted HTTP authentication traffic between a staff workstation (`192.168.10.45`) and an internal staff portal (`192.168.10.20`). The objective was to determine whether sensitive login credentials could be recovered from network traffic using Wireshark.

Analysis of the supplied network capture identified **255 packets**. Applying the display filter `http` revealed authentication requests using the HTTP `POST` method, directed towards the `/login` endpoint.

Further examination using `http.request.method == "POST"` identified two login attempts originating from `192.168.10.45`. The first attempt was unsuccessful, while the second successfully authenticated the user.

By inspecting the **HTML Form URL Encoded** section within the packet details, the investigation identified the username `farhan.k` and the plaintext password `Mango#2026` used during the successful authentication attempt.

The investigation demonstrated that transmitting authentication credentials over unencrypted HTTP exposes sensitive information to individuals capable of capturing and inspecting network communications.

### Investigation Summary

| Investigation Item | Result |
|---|---|
| Packets captured | 255 |
| Staff workstation IP | `192.168.10.45` |
| Staff portal server IP | `192.168.10.20` |
| Application protocol | HTTP |
| HTTP request method | POST |
| Authentication endpoint | `/login` |
| Login attempts | 2 |
| Failed attempts | 1 |
| Successful attempts | 1 |
| Username | `farhan.k` |
| Successful login password | `Mango#2026` (simulated) |
| Credential location | HTML Form URL Encoded |
| Recommended security control | HTTPS |

### Security Classification

**Plaintext Credential Exposure Through Unencrypted HTTP Authentication**

The investigation identified a confidentiality weakness in the staff portal's authentication process.

Because the portal transmitted login requests using HTTP rather than HTTPS, the username and password were visible within the captured network packets.

Wireshark's packet inspection capabilities demonstrated that authentication credentials could be extracted directly from the HTTP POST request without requiring decryption.

Although the investigation did not demonstrate account compromise by an external attacker, the exposed credentials represent a potential security risk if intercepted by an unauthorised party.

### Security Implications

Transmitting authentication credentials over unencrypted HTTP increases the risk of credential interception, unauthorised account access and subsequent compromise of internal systems.

Attackers with access to the relevant network traffic could potentially recover usernames and passwords, enabling credential misuse or further attacks against connected organisational services.

Organisations should enforce **HTTPS using TLS** across authentication pages and associated application endpoints to protect credentials during transmission.

Additional security measures, including multi-factor authentication, secure session management, password policies and monitoring for suspicious authentication attempts, can reduce the impact of credential exposure.

However, these measures should complement HTTPS rather than replace transport encryption.

### Evidence

- Wireshark packet capture showing 255 packets – pending screenshot
- HTTP traffic filter identifying login requests – pending screenshot
- HTTP POST requests directed towards `/login` – pending screenshot
- HTML Form URL Encoded showing submitted credentials – pending screenshot (password redacted)
- Comparison with encrypted HTTPS traffic – pending screenshot
- Official Networkwalks completion result – pending upload

### Skills Demonstrated

- Network Traffic Analysis
- HTTP Protocol Investigation
- Wireshark Display Filtering
- HTTP POST Request Inspection
- Authentication Traffic Analysis
- Plaintext Credential Exposure Detection
- Security Control Evaluation
- SOC Investigation Documentation
