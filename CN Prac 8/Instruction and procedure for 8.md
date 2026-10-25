# Practical No. 8

**Aim:** To use Wireshark to display the operation of TCP/IP layers, specifically the Data Link Layer, MAC addresses, and ARP (IP and MAC address binding).

### Software Required
- Wireshark
- Windows Operating System
- Active Network Connection

### Theory

**1. Wireshark:** Wireshark is a network packet analyzer used to capture and examine network traffic.

**2. Data Link Layer:** The Data Link Layer is responsible for transferring data between devices on the same network using MAC addresses.

**3. MAC Address:** A MAC (Media Access Control) address is a unique hardware address assigned to a network interface. It is generally 48 bits long.

**4. ARP (Address Resolution Protocol):** ARP is used to find the MAC address associated with a known IPv4 address on a local network.

**5. ARP Request:** A device sends an ARP request to find the MAC address of a particular IP address.

**6. ARP Reply:** The device owning that IP address responds with its MAC address.

### Procedure

1. Open Wireshark.
2. Select the active Wi-Fi network interface.
3. Start capturing network packets.
4. Open Command Prompt and execute:

   `ping 192.168.31.1`

5. Stop the packet capture in Wireshark.
6. Enter `arp` in the display filter.
7. Select an ARP Request packet and expand the Ethernet II and Address Resolution Protocol sections.
8. Observe the source and destination MAC addresses, sender IP, and target IP.
9. Select an ARP Reply packet and observe its details.
10. Record the captured information.

### Observation

**ARP Request**

| Parameter | Observed Value |
|---|---|
| Hardware Type | Ethernet (1) |
| Protocol Type | IPv4 (0x0800) |
| Opcode | Request (1) |
| Sender IP | 192.168.31.1 |
| Sender MAC | 3C:55:DB:B7:70:0D |
| Target IP | 192.168.31.109 |
| Target MAC | 00:00:00:00:00:00 |

**ARP Reply**

| Parameter | Observed Value |
|---|---|
| Hardware Type | Ethernet (1) |
| Protocol Type | IPv4 (0x0800) |
| Opcode | Reply (2) |
| Sender IP | 192.168.31.109 |
| Sender MAC | D0:39:57:CF:DC:C7 |
| Target IP | 192.168.31.1 |
| Target MAC | 3C:55:DB:B7:70:0D |

### Output

Wireshark successfully captured ARP Request and ARP Reply packets, displaying the corresponding IP addresses and MAC addresses.

**Screenshots to Attach:**
1. Wireshark ARP Request packet details.
2. Wireshark ARP Reply packet details.

### Result

Successfully captured and analyzed ARP packets using Wireshark and understood the mapping between IPv4 addresses and MAC addresses at the Data Link Layer.

### Conclusion

This practical demonstrated how ARP resolves an IPv4 address to a MAC address and how Wireshark can be used to analyze Ethernet frames and ARP communication.
