## Investigation Results

**Status:** Investigation findings documented – completion evidence pending

**Final Score:** Pending verification

### Key Findings

The investigation examined unencrypted TCP communications between a staff workstation (`192.168.10.45`) and an internal chat server (`192.168.10.20`). The objective was to determine whether sensitive information was being transmitted through an outdated office messaging application.

Analysis of the supplied network capture identified **246 packets**. Using Wireshark's **Statistics → Conversations** feature, TCP port `5000` was identified as the communication port used by the office chat application.

Applying the display filter `tcp.port == 5000` revealed that the staff workstation initiated the connection. Further examination using **Follow TCP Stream** identified the conversation in **TCP Stream 5**, containing **413 bytes** of reconstructed communication.

The conversation involved a staff member named Ali from the Accounts department, who reported being unable to access the Finance shared drive. During the conversation, IT support disclosed a temporary password (`Tiger#4821`) and a guest Wi-Fi password (`BlueHarbor77`).

Wireshark displayed the client messages in red and the server responses in blue, allowing the direction of communication to be distinguished.

These findings demonstrate how unencrypted messaging applications can expose sensitive information to individuals capable of intercepting network traffic.

### Investigation Summary

| Investigation Item | Result |
|---|---|
| Packets captured | 246 |
| Staff workstation IP | `192.168.10.45` |
| Chat server IP | `192.168.10.20` |
| Application port | TCP 5000 |
| TCP stream number | 5 |
| Conversation size | 413 bytes |
| Staff member | Ali (Accounts) |
| Affected shared drive | Finance |
| Temporary password | `Tiger#4821` (simulated) |
| Guest Wi-Fi password | `BlueHarbor77` (simulated) |
| Client message colour | Red |
| Server message colour | Blue |

### Security Classification

**Sensitive Credential Disclosure Through Unencrypted TCP Communications**

The investigation identified sensitive authentication information being transmitted in readable text through an internal office chat application.

Because the application did not encrypt its communications, the reconstructed TCP stream exposed both a temporary account password and a guest Wi-Fi password.

This represents a potential confidentiality weakness, as individuals with access to captured network traffic could recover sensitive information without needing to decrypt the communication.

### Security Implications

Transmitting credentials through unencrypted messaging systems creates a risk of credential interception, unauthorised access and further compromise of internal resources.

The exposed temporary password could potentially be misused to access an account, while disclosure of the guest Wi-Fi password could allow unauthorised individuals to connect to the guest network, depending on additional access controls.

Organisations should replace outdated plaintext communication tools with encrypted alternatives, enforce TLS for sensitive communications and prohibit the sharing of passwords through insecure messaging channels.

Additional controls, including multi-factor authentication, credential rotation and staff security awareness training, can reduce the likelihood and impact of credential exposure.

### Evidence

- Wireshark packet capture showing 246 packets – pending screenshot
- TCP Conversations statistics identifying port 5000 – pending screenshot
- Display filter `tcp.port == 5000` – pending screenshot
- Follow TCP Stream 5 showing reconstructed communications – pending screenshot (credentials redacted)
- Official Networkwalks completion result – pending upload

### Skills Demonstrated

- Network Traffic Analysis
- TCP Conversation Identification
- Wireshark Display Filtering
- TCP Stream Reconstruction
- Client–Server Communication Analysis
- Plaintext Credential Exposure Detection
- SOC Investigation Reporting
