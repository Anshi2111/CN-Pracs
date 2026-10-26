

### After above step,i cant do on laptop due to dhcp connection so continue on college pc ,u just need to add one more ip address,follow procedure
I opened Wi-Fi Properties and navigated to Internet Protocol Version 4 (TCP/IPv4) → Properties → Advanced. However, the **Add** button under IP addresses was disabled because the Wi-Fi adapter was configured to obtain its IP address automatically using DHCP. Therefore, I could not add a secondary IP address without changing the existing network configuration.

### Procedure to Perform on a College PC Using Ethernet

1. Open **Run** (`Win + R`), type `ncpa.cpl`, and press Enter.
2. Right-click the connected **Ethernet** adapter and select **Properties**.
3. Select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**.
4. Select **Use the following IP address** and enter the IP address and subnet mask assigned by the lab instructor.
5. Click **Advanced**. Under **IP addresses**, click **Add**.
6. Enter the secondary IP address and subnet mask, then click **Add**.
7. Click **OK** to save the settings.
8. Open Command Prompt and execute:

```cmd
ipconfig
```

9. Verify that both IPv4 addresses appear under the Ethernet adapter.

### Example IP Address Configuration

Use these values **only on an isolated lab network where the instructor confirms that the addresses are available**.

- Primary IP address: `192.168.10.10`
- Subnet mask: `255.255.255.0`
- Secondary IP address: `192.168.10.11`
- Secondary subnet mask: `255.255.255.0`
- Default gateway: Leave unchanged unless instructed otherwise.

Both addresses belong to the same `192.168.10.0/24` network. Do not apply these example values to the college's live network without approval.

### Expected Verification

The `ipconfig` output should show the configured IPv4 address for the Ethernet adapter. Confirm the secondary address in **Advanced TCP/IP Settings**, because `ipconfig` output can vary by Windows version and configuration.

### Result
The procedure describes how to configure multiple IPv4 addresses on one Ethernet adapter. Actual configuration and verification should be completed on the college PC using instructor-approved network settings.
