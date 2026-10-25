# Practical No. 9

**Aim:** To use Wireshark to study the Network Layer, including IP packet headers, fragmentation, and ICMP Query and Echo messages.

### Software Required
- Wireshark
- Windows Operating System
- Active Internet Connection

### Theory

**1. Internet Protocol (IP):** IP is a Network Layer protocol responsible for addressing and routing packets from source to destination.

**2. IP Header:** The IP header contains information such as source address, destination address, TTL, protocol, and fragmentation details.

**3. Fragmentation:** Fragmentation is the process of dividing an IP packet into smaller fragments when it exceeds the maximum transmission unit (MTU) of a network.

**4. ICMP:** Internet Control Message Protocol is used for network diagnostics and error reporting.

**5. ICMP Echo Request:** An ICMP Echo Request is sent by the `ping` command to check whether a destination is reachable. Its Type is 8.

**6. ICMP Echo Reply:** The destination responds with an ICMP Echo Reply if it receives and processes the request. Its Type is 0.

### Procedure

1. Open Wireshark and select the active Wi-Fi interface.
2. Start packet capture.
3. Open Command Prompt and execute:

   `ping -n 4 8.8.8.8`

4. Stop the capture after the ping completes.
5. Enter `icmp` in the Wireshark display filter.
6. Select an Echo Request packet and expand the Internet Protocol Version 4 section.
7. Observe the source IP, destination IP, TTL, protocol, and fragmentation fields.
8. Expand the Internet Control Message Protocol section and observe the message type and code.
9. Select an Echo Reply packet and examine its IP and ICMP header details.

### Observations

**A. IP Header — Echo Request**

| Field | Observed Value |
|---|---|
| Source IP Address | 192.168.31.109 |
| Destination IP Address | 8.8.8.8 |
| Time to Live (TTL) | 128 |
| Protocol | ICMP (1) |
| Fragment Offset | 0 |
| Header Checksum | 0xA80B |

**B. ICMP Echo Request**

| Field | Observed Value |
|---|---|
| Type | Echo Request (8) |
| Code | 0 |
| Identifier | 1 (0x0001) |
| Checksum | 0x4D54 |

**C. ICMP Echo Reply**

| Field | Observed Value |
|---|---|
| Source IP Address | 8.8.8.8 |
| Destination IP Address | 192.168.31.109 |
| Time to Live (TTL) | 111 |
| Protocol | ICMP (1) |
| Type | Echo Reply (0) |
| Code | 0 |
| Checksum | 0x5554 |

### Output

Wireshark captured ICMP Echo Request and Echo Reply packets. The IP headers displayed the source and destination addresses, TTL, protocol, and fragmentation information.

### Result

Successfully captured and analyzed IP packet headers and ICMP Echo Request and Echo Reply messages using Wireshark.

### Conclusion

This practical demonstrated how Wireshark can be used to inspect Network Layer IP headers and study ICMP messages for network connectivity testing.

**Note:** The capture showed a fragment offset of 0, but this alone does not prove that fragmentation occurred. To demonstrate actual fragmentation, fragmented IP packets would need to be captured separately.
