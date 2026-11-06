## Investigation Results

**Status:** Investigation findings documented – completion evidence pending

**Final Score:** Pending verification

### Key Findings

The investigation examined Voice over Internet Protocol (VoIP) communications within a simulated corporate network. The objective was to identify a recorded telephone conversation, reconstruct the call using Wireshark and determine whether sensitive financial information could be recovered from unencrypted voice traffic.

Analysis of the supplied network capture identified **1,051 packets**. Using Wireshark's **Statistics → Protocol Hierarchy** feature and the `sip` display filter, the investigation identified Session Initiation Protocol (SIP) messages responsible for establishing the telephone call, including `INVITE`, `180 Ringing` and `200 OK`.

Further examination using the `rtp` display filter identified approximately **800 Real-time Transport Protocol (RTP) packets** carrying the voice communications. The RTP payload used the **G.711 PCMU codec**, which enabled reconstruction and playback of the conversation.

By examining the SIP `INVITE` message, the caller was identified as Ali Raza, using extension `101` from `192.168.10.45`. The call was answered by Sara at the Payments desk, using extension `202`.

Using Wireshark's **Telephony → VoIP Calls → Play Streams** functionality, the simulated conversation could be replayed. The lab's supplied recording disclosed payment-card information, including the final four digits `2394` and an expiry date of `09/28`.

These findings demonstrate how unencrypted VoIP traffic can expose confidential voice communications and sensitive payment information to individuals capable of capturing the relevant network packets.

### Investigation Summary

| Investigation Item | Result |
|---|---|
| Packets captured | 1,051 |
| Call signalling protocol | SIP |
| SIP signalling port | UDP 5060 |
| Voice transport protocol | RTP |
| Approximate RTP packets | 800 |
| Audio codec | G.711 PCMU |
| Caller | Ali Raza |
| Caller extension | 101 |
| Caller IP address | `192.168.10.45` |
| Call recipient | Sara (Payments desk) |
| Recipient extension | 202 |
| Payment card last four digits | 2394 (simulated) |
| Card expiry date | 09/28 (simulated) |
| Investigation technique | VoIP Calls and RTP stream playback |
| Recommended security control | SRTP with TLS-protected SIP signalling |

### Security Classification

**Sensitive Financial Information Disclosure Through Unencrypted VoIP Communications**

The investigation identified a confidentiality weakness affecting the simulated organisation's VoIP communications.

Although SIP was used to establish the telephone session, the voice content was transmitted using RTP without encryption.

As a result, Wireshark could reconstruct and replay the conversation, revealing confidential payment information exchanged between the caller and the Payments desk.

The successful reconstruction of the audio demonstrates that access to unencrypted RTP traffic may allow an unauthorised observer to listen to conversations and recover sensitive information.

However, the lab does not establish that an external attacker intercepted the call or that the disclosed payment details were subsequently misused.

### Security Implications

Unencrypted VoIP communications create potential risks to the confidentiality of business conversations, customer information and financial transactions.

Attackers with access to relevant network traffic may be able to capture RTP packets, reconstruct audio streams and obtain sensitive information discussed during telephone calls.

In this scenario, the disclosure of payment-card information illustrates the importance of protecting voice communications and limiting the collection or transmission of sensitive financial data.

Organisations should implement **Secure Real-time Transport Protocol (SRTP)** to encrypt voice traffic and use **TLS** to protect SIP signalling where supported.

Additional security measures should include restricting access to VoIP network segments, monitoring suspicious traffic, enforcing appropriate access controls and implementing secure payment-handling procedures.

Where payment-card information is processed over telephone systems, organisations should also assess applicable PCI DSS requirements and consider secure payment solutions that prevent sensitive card information from being exposed to unnecessary systems or personnel.

### Evidence

- Wireshark packet capture showing 1,051 packets – pending screenshot
- SIP traffic displaying INVITE, Ringing and OK messages – pending screenshot
- SIP INVITE identifying caller details – pending screenshot
- RTP traffic and G.711 PCMU codec identification – pending screenshot
- Telephony → VoIP Calls showing the detected call – pending screenshot
- RTP stream playback demonstrating audio reconstruction – pending screenshot (payment details redacted)
- Official Networkwalks completion result – pending upload

### Skills Demonstrated

- Network Traffic Analysis
- VoIP Security Investigation
- SIP Protocol Analysis
- RTP Packet Inspection
- Audio Codec Identification
- VoIP Call Reconstruction
- Network-Based Information Disclosure Detection
- Sensitive Financial Data Exposure Assessment
- Security Control Evaluation
- SOC Investigation Reporting
