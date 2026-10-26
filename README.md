# Network Traffic Analysis & Threat Detection Using Wireshark

**Hands-on Cybersecurity Project | SOC Analyst L1 | Blue Team**

## 1. Project Overview

This project demonstrates hands-on network traffic analysis and basic threat detection using Wireshark, Kali Linux, and Nmap.

The objective was to capture, inspect, and interpret network packets to understand normal network communications and identify traffic patterns associated with port scanning.

Four practical labs were completed in a controlled virtual environment.

## 2. Objectives

- Capture and analyze ICMP traffic.
- Investigate DNS queries and responses.
- Examine the TCP Three-Way Handshake.
- Identify TCP SYN and RST-ACK flags.
- Detect simulated SYN port scanning activity.
- Document technical findings and preserve packet capture evidence.

## 3. Tools and Environment

| Tool | Purpose |
|---|---|
| Kali Linux | Security testing environment |
| Wireshark 4.6.6 | Packet capture and protocol analysis |
| Nmap 7.99 | Controlled port scanning |
| Oracle VirtualBox | Virtualization platform |
| GitHub | Project documentation and portfolio |

## 4. Lab 01 — ICMP Traffic Analysis

**Objective:** Analyze ICMP Echo Request and Echo Reply packets.

A connectivity test was performed using the following command:

`ping -c 4 1.1.1.1`

Wireshark was used to inspect the resulting ICMP traffic.

**Findings:**
- Four ICMP Echo Replies were received.
- The connectivity test reported 0% packet loss.
- Request and reply packets were identified.
- Source and destination IP addresses were examined.

**Conclusion:** The test demonstrated successful ICMP communication with the remote destination.
### Evidence — ICMP Traffic Analysis

The following screenshots demonstrate the ICMP
connectivity test and packet inspection performed
during the laboratory.

![ICMP Connectivity Test](screenshots/02-icmp-connectivity-test.jpeg)

![Wireshark ICMP Packet Capture](screenshots/03.0-wireshark-icmp-capture.jpeg)

![ICMP Packet Details](screenshots/04-icmp-packet-details.jpeg)

## 5. Lab 02 — DNS Traffic Analysis

**Objective:** Examine DNS resolution and identify IPv4 and IPv6 records.

DNS traffic for `example.com` was captured and inspected.

**Findings:**
- DNS queries and responses were identified.
- IPv4 addresses were observed in A records.
- IPv6 addresses were observed in AAAA records.
- DNS response TTL values were examined.
- The captured AAAA response contained two IPv6 addresses with a TTL of 105 seconds.

**Conclusion:** The analysis demonstrated how DNS translates domain names into IP addresses and how these results can be inspected during network investigations.

### Evidence — DNS Traffic Analysis

The following screenshots demonstrate DNS query and
response analysis, including IPv4 and IPv6 records.

![DNS Query Analysis](screenshots/05-dns-query-analysis.jpeg)

![DNS Response Details](screenshots/06-dns-response-details.jpeg)

![DNS IPv6 Analysis](screenshots/07-dns-ipv6-analysis.jpeg)

## 6. Lab 03 — TCP Three-Way Handshake

**Objective:** Understand how a TCP connection is established.

A TCP connection between `10.0.2.15` and `104.20.23.154` was examined.

**Findings:**

| Stage | TCP Flags | Description |
|---|---|---|
| 1 | SYN | Client initiates connection |
| 2 | SYN, ACK | Server acknowledges the request |
| 3 | ACK | Client completes the handshake |

The captured connection used destination port 80 and included HTTP traffic.

**Conclusion:** The three TCP handshake stages were successfully identified and verified through packet inspection.

### Evidence — TCP Three-Way Handshake Analysis

The following screenshots demonstrate the three
stages of the TCP connection establishment process.

![TCP Three-Way Handshake](screenshots/08-tcp-three-way-handshake.jpeg)

![TCP SYN Flag Analysis](screenshots/09-tcp-syn-flags.jpeg)

![TCP SYN-ACK Flag Analysis](screenshots/10-tcp-syn-ack-flags.jpeg)

![TCP Final ACK Analysis](screenshots/11-tcp-final-ack.jpeg)

## 7. Lab 04 — SYN Port Scan Detection

**Objective:** Identify traffic patterns associated with TCP SYN port scanning.

A controlled Nmap scan was executed against the local loopback interface.

**Command:**

`sudo nmap -sS -Pn -p 20-30 127.0.0.1`

**Findings:**
- Eleven TCP ports were scanned.
- SYN packets were observed across multiple destination ports.
- RST-ACK responses were captured.
- Nmap reported the scanned ports as closed.
- Wireshark displayed 22 TCP packets associated with the scan.

**Conclusion:** The experiment demonstrated how a SYN port scan can produce recognizable network traffic patterns.

Because the activity was generated intentionally against the local machine, it was classified as authorized laboratory activity rather than a security incident.

### Evidence — SYN Port Scan Detection

The following screenshots demonstrate the Nmap
installation verification and the detection of
TCP SYN scanning activity using Wireshark.

![Nmap Version Verification](screenshots/12-nmap-version.jpeg)

![TCP SYN Port Scan Detection](screenshots/13-nmap-syn-scan-detection.jpeg)

## 8. Security Analysis

The laboratory demonstrated the importance of distinguishing normal network communication from potentially suspicious behavior.

Repeated SYN packets directed toward multiple ports can indicate reconnaissance activity. However, such patterns alone are insufficient to confirm malicious intent.

Additional investigation would be required in a production SOC environment, including source identification, asset context, authorization checks, and correlation with other security events.

## 9. Skills Demonstrated

- Network traffic analysis
- Packet inspection
- ICMP and DNS protocol analysis
- TCP flag interpretation
- Network reconnaissance detection
- Wireshark display filtering
- Basic security investigation
- Technical documentation

## 10. Conclusion

This project strengthened my practical understanding of network protocols and introduced a structured approach to analyzing network traffic from a defensive security perspective.

By completing four hands-on investigations, I gained experience examining packet-level evidence, identifying TCP connection behavior, and recognizing traffic patterns associated with port scanning.

These skills provide a foundation for further development in SOC monitoring, network security analysis, and incident investigation.

---

**Project Type:** Personal Cybersecurity Lab

**Focus:** SOC Analyst L1 / Junior Cybersecurity Analyst

**Environment:** Controlled Virtual Laboratory