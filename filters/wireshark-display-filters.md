# Wireshark Display Filters — SOC Network Analysis

This document contains Wireshark display filters used during the network traffic analysis project, along with additional filters relevant to basic SOC investigations.

## 1. ICMP Traffic

```text
icmp
```

Displays ICMP packets, including Echo Requests and Echo Replies.

## 2. DNS Traffic

```text
dns
```

Displays DNS queries and responses.

## 3. TCP Traffic

```text
tcp
```

Displays TCP packets for connection and flag analysis.

## 4. TCP SYN Packets

```text
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

Displays initial TCP SYN packets, useful when investigating connection attempts and possible port scanning.

## 5. TCP SYN-ACK Packets

```text
tcp.flags.syn == 1 && tcp.flags.ack == 1
```

Displays TCP SYN-ACK responses during connection establishment.

## 6. TCP Reset Packets

```text
tcp.flags.reset == 1
```

Displays TCP reset packets, which may indicate rejected or terminated connections.

## 7. DNS Queries for a Specific Domain

```text
dns.qry.name == "example.com"
```

Displays DNS packets associated with queries for the specified domain.

## 8. TCP Port 80

```text
tcp.port == 80
```

Displays TCP traffic associated with port 80.

## 9. HTTP or TCP Payload Traffic

```text
http || tcp.len > 0
```

Displays HTTP packets or TCP segments containing payload data.

---

**Note:** These filters support packet-level investigation. A matching packet or traffic pattern does not independently confirm malicious activity. Findings must be evaluated within the appropriate security context.