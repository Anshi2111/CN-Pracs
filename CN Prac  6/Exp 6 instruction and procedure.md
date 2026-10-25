# Practical 6: IP Addressing, Subnetting and Subnet Masks

## Aim
To configure IP addresses and subnet masks and understand subnetting using Cisco Packet Tracer.

## Requirements
- Cisco Packet Tracer
- Two routers
- Two PCs
- Ethernet connections

## Theory
An IP address uniquely identifies a device on a network. A subnet mask separates the network portion from the host portion of an IP address.

Subnetting is the process of dividing a network into smaller networks by borrowing bits from the host portion.

CIDR notation represents the number of network bits. For example, `/24` corresponds to the subnet mask `255.255.255.0`, while `/30` corresponds to `255.255.255.252`.

## IP Addressing Table

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| PC0 | FastEthernet | 192.168.1.2 | 255.255.255.0 |
| Router2 | G0/0 | 192.168.1.1 | 255.255.255.0 |
| Router2 | G0/1 | 10.0.0.1 | 255.255.255.252 |
| Router3 | G0/0 | 192.168.2.1 | 255.255.255.0 |
| Router3 | G0/1 | 10.0.0.2 | 255.255.255.252 |
| PC1 | FastEthernet | 192.168.2.2 | 255.255.255.0 |

## Subnet Calculations

**1. Network 1: 192.168.1.0/24**
- Subnet mask: 255.255.255.0
- Network address: 192.168.1.0
- First usable address: 192.168.1.1
- Last usable address: 192.168.1.254
- Broadcast address: 192.168.1.255
- Total addresses: 256
- Usable host addresses: 254

**2. Network 2: 10.0.0.0/30**
- Subnet mask: 255.255.255.252
- Network address: 10.0.0.0
- First usable address: 10.0.0.1
- Last usable address: 10.0.0.2
- Broadcast address: 10.0.0.3
- Total addresses: 4
- Usable host addresses: 2

**3. Network 3: 192.168.2.0/24**
- Subnet mask: 255.255.255.0
- Network address: 192.168.2.0
- First usable address: 192.168.2.1
- Last usable address: 192.168.2.254
- Broadcast address: 192.168.2.255
- Total addresses: 256
- Usable host addresses: 254

## Procedure
1. Open Cisco Packet Tracer and create a topology containing two PCs connected to two routers.
2. Assign the IP addresses and subnet masks according to the IP addressing table.
3. Configure the default gateways of both PCs.
4. Configure static routes on both routers to enable communication between the LANs.
5. Calculate the network address, usable host range and broadcast address for each network.
6. Open PC0's Command Prompt and ping `192.168.2.2`.
7. Verify that the ping receives successful replies.

## Expected Output
PC0 should successfully communicate with PC1 through the two routers. The subnet calculations should identify the network address, usable host range and broadcast address for each network.

## Result
IP addressing and subnet mask calculations were studied using Cisco Packet Tracer. Connectivity between the two PCs was verified successfully.

## Conclusion
IP addresses and subnet masks help identify network and host portions of an IP address. CIDR notation represents the number of network bits, and subnetting allows networks to be divided into smaller networks.
