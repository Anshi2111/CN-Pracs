# Practical 5: Static Routing in Cisco Packet Tracer

## Aim
To configure static routing between two different networks using Cisco Packet Tracer and verify connectivity using the ping command.

## Overview
This practical demonstrates communication between two PCs connected to different networks through two routers. Static routes are configured manually to enable communication between the networks.

## Requirements
- Cisco Packet Tracer
- 2 Routers
- 2 PCs
- Copper cables

## Network Topology
```text
PC0 ─── Router2 ─── Router3 ─── PC1
```

## IP Addressing

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| PC0 | FastEthernet0 | 192.168.1.2 | 255.255.255.0 |
| Router2 | GigabitEthernet0/0 | 192.168.1.1 | 255.255.255.0 |
| Router2 | GigabitEthernet0/1 | 10.0.0.1 | 255.255.255.252 |
| Router3 | GigabitEthernet0/0 | 192.168.2.1 | 255.255.255.0 |
| Router3 | GigabitEthernet0/1 | 10.0.0.2 | 255.255.255.252 |
| PC1 | FastEthernet0 | 192.168.2.2 | 255.255.255.0 |

## Static Routing Configuration

### Router2
- Destination Network: `192.168.2.0`
- Subnet Mask: `255.255.255.0`
- Next Hop: `10.0.0.2`

### Router3
- Destination Network: `192.168.1.0`
- Subnet Mask: `255.255.255.0`
- Next Hop: `10.0.0.1`

## Procedure
1. Place two routers and two PCs in Cisco Packet Tracer.
2. Connect the devices using appropriate cables.
3. Configure the IP addresses and subnet masks on the router interfaces.
4. Enable the router interfaces.
5. Configure the IP address and default gateway on both PCs.
6. Add the required static routes on both routers.
7. Open PC0's Desktop → Command Prompt.
8. Execute `ping 192.168.2.2` to test connectivity with PC1.
9. Verify the replies and packet loss.

## Expected Output
The ping command should receive replies from `192.168.2.2`, indicating that PC0 can communicate with PC1 through the routers.

## Result
Static routing was configured in Cisco Packet Tracer, and connectivity between the two PCs was verified using the ping command.

## Conclusion
Static routing allows routers to forward packets to remote networks using manually configured routes. Successful ping communication confirms connectivity between the configured networks.

## Viva Questions
1. **What is static routing?**  
   Static routing is the manual configuration of routes by a network administrator.

2. **What is a
