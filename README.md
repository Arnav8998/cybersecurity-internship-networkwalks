# Cybersecurity Internship – Networkwalks

## Project Overview
This repository documents my practical cybersecurity internship work with Networkwalks, focusing on Linux administration, network configuration, cloud-based lab environments and troubleshooting.

## Week 1 – Kali Linux Lab Setup

### Objective
Configure a cybersecurity testing environment with Kali Linux and a static IPv4 address of `10.0.0.2/24`.

### Tools and Technologies
- Kali Linux
- Microsoft Azure Lab Services
- Remote Desktop
- NetworkManager (`nmcli`)
- Linux networking commands
- 7-Zip and AppsAnywhere

### Implementation
1. Investigated institutional software installation restrictions.
2. Accessed an approved version of 7-Zip through AppsAnywhere.
3. Investigated the availability of VirtualBox and Hyper-V.
4. Used a university-provided Azure-hosted Kali Linux environment as an alternative.
5. Configured static IPv4 addressing using `nmcli`.
6. Verified the assigned IP address using `ip addr show eth0`.

### Key Commands
```bash
nmcli connection show
nmcli connection modify "Wired connection 1" ipv4.addresses 10.0.0.2/24 ipv4.method manual
nmcli connection modify "Wired connection 1" ipv4.gateway 10.0.0.1
nmcli connection up "Wired connection 1"
ip addr show eth0
```

### Results
Successfully configured and verified `10.0.0.2/24` on the Kali Linux `eth0` interface.

### Limitations
The documented setup used Azure Lab Services rather than the prescribed local VirtualBox environment. The available evidence does not establish completion of all original VirtualBox requirements.

### Supporting Documentation
See the Week 1 submission report in this repository for screenshots and technical explanations.

## Skills Demonstrated
Linux Administration | IPv4 Networking | Network Troubleshooting | Cloud Lab Environments | Technical Documentation
