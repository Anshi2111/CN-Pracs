# Practical 7: Perform Network Discovery Using Nmap

## Aim
To perform network discovery using Nmap and identify active hosts, open ports, and operating system information.

## Requirements
- Windows 11
- Nmap / Zenmap
- Computer with a network interface

## Theory
Nmap (Network Mapper) is a network discovery and security auditing tool. It is used to identify active hosts, scan open ports, detect services, and estimate the operating system running on a target machine.

Zenmap is the graphical user interface for Nmap that allows users to perform scans by selecting a target and scan profile.

### Types of Scans Performed
1. **Intense Scan:** Scans ports and attempts to detect services and operating system information.
2. **Ping Scan:** Checks whether a target host is up without performing a port scan.

## Procedure

### Part A: Intense Scan
1. Open Zenmap on Windows.
2. Enter `127.0.0.1` in the Target field. This address refers to the local computer.
3. Select the **Intense Scan** profile.
4. Click **Scan** and wait for the scan to complete.
5. Observe the open ports, service information, and operating system detection results.
6. Save a screenshot of the output.

### Part B: Ping Scan
1. Keep the target as `127.0.0.1`.
2. Select the **Ping Scan** profile.
3. Click **Scan**.
4. Observe the result showing whether the host is up.
5. Save a screenshot of the output.

## Commands Used

**Intense Scan:**
`nmap -T4 -A -v 127.0.0.1`

**Ping Scan:**
`nmap -sn 127.0.0.1`

## Observations and Output

### Intense Scan
- Target IP address: `127.0.0.1`
- Host: Localhost
- Host status: Up
- Open TCP ports observed: `135`, `445`, and `3306`
- Operating system detected: Microsoft Windows 11

### Ping Scan
- Target IP address: `127.0.0.1`
- Host status: Up
- Scan completed successfully.
- One IP address was scanned, and one host was found up.

## Result
Network discovery was successfully performed using Nmap through Zenmap. The intense scan identified open ports and operating system information, while the ping scan confirmed that the local host was active.

## Conclusion
Nmap is a useful tool for network discovery, port scanning, service detection, and operating system identification. Zenmap provides a graphical interface for performing these scans.
