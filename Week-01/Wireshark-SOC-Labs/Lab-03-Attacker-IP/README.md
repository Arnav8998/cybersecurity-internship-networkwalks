## Investigation Results

**Status:** Completed – 6 November 2026

**Final Score:** 100/100 (10/10 tasks correct)

### Key Findings

The investigation identified suspicious TCP traffic originating from `192.168.10.66` and targeting the web server at `192.168.10.20`.

Analysis of the supplied packet capture identified 309 packets, including 73 packets displayed using the TCP SYN filter. The suspected attacker probed 40 destination ports, using source port `52311`.

The server responded with SYN-ACK packets on ports 22, 80 and 443, indicating that these ports were open. The remaining 37 probed ports returned RST-ACK responses, indicating closed ports.

### Attack Classification

**TCP Port Scan**

The activity is consistent with network reconnaissance because a single source attempted connections to multiple destination ports within a short period.

### Security Implications

Port scanning can help an attacker identify exposed services and potential entry points for subsequent attacks. However, the scan alone does not establish that a service was exploited or that the server was compromised.

### Evidence

- Official Networkwalks completion result: 100/100
- Wireshark packet capture screenshot
- TCP SYN analysis screenshot (if captured)

### Skills Demonstrated

- TCP/IP traffic analysis
- Wireshark display filtering
- Attacker and target IP identification
- TCP flag interpretation
- Port scanning detection
- SOC investigation reporting
