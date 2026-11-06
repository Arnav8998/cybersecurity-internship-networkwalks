## Investigation Results

**Status:** Investigation findings documented – completion evidence pending

**Final Score:** Pending verification

### Key Findings

The investigation examined HTTP network traffic between a staff workstation (`192.168.10.45`) and the company intranet server (`192.168.10.20`). The objective was to identify sensitive information hidden within a web page by reconstructing TCP communications using Wireshark.

Analysis of the supplied capture identified **282 packets**. By applying the `http` display filter and using the **Follow TCP Stream** feature, the investigation identified a hidden HTML comment within the `/staff.html` page, carried in **TCP Stream 7**.

The comment contained an access code, `Falcon-9921`, and the IP address of a backup server, `192.168.10.77`. The information appeared in the server's HTTP response, demonstrating that hidden HTML comments can still be recovered through network traffic inspection.

Further investigation identified an HTTP `200 OK` response and a downloaded text file, `/download/report.txt`, containing a report attributed to Nadia.

### Investigation Summary

| Investigation Item | Result |
|---|---|
| Packets captured | 282 |
| Staff workstation | `192.168.10.45` |
| Intranet server | `192.168.10.20` |
| Page containing hidden information | `/staff.html` |
| TCP stream number | 7 |
| Information location | HTML comment |
| Access code | `Falcon-9921` |
| Backup server IP | `192.168.10.77` |
| Communication direction | Server to client |
| HTTP response status | `200 OK` |
| Downloaded file | `report.txt` |
| Report author | Nadia |

### Security Classification

**Sensitive Information Disclosure Through HTTP Content**

The investigation demonstrates how information embedded within HTML comments can remain hidden from normal browser presentation while still being transmitted to clients.

Although the activity does not establish that an attacker exploited the server, the exposed access code and internal backup server address represent potential information disclosure risks.

### Security Implications

Exposing sensitive information in HTML comments may allow unauthorised users to discover internal infrastructure details or credentials intended to remain confidential.

Furthermore, unencrypted HTTP communications may expose transmitted content to parties capable of observing the network traffic.

Organisations should avoid embedding secrets in client-accessible web content, remove unnecessary internal infrastructure references and use HTTPS to protect communications in transit.

### Evidence

- Wireshark packet capture showing 282 packets – pending screenshot
- HTTP display filter and `/staff.html` traffic – pending screenshot
- Follow TCP Stream 7 showing the hidden HTML comment – pending screenshot
- HTTP download request for `/download/report.txt` – pending screenshot
- Official Networkwalks completion result – pending upload

### Skills Demonstrated

- HTTP Traffic Analysis
- TCP Stream Reconstruction
- Wireshark Display Filtering
- HTML Comment Inspection
- Sensitive Information Disclosure Identification
- HTTP Request and Response Analysis
- SOC Investigation Documentation
