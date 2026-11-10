Task 4: Setup and Use a Firewall on Windows

Description

This project focuses on configuring and managing Windows Defender Firewall in Windows 11. The practical involved exploring existing inbound rules, creating a custom rule to block incoming TCP traffic on port 23, verifying its configuration, and removing the temporary rule.

Objectives

- Understand the basic concept and purpose of a firewall.
- Explore Windows Defender Firewall.
- Inspect existing inbound firewall rules.
- Create a rule to block incoming traffic on a specific port.
- Perform basic connectivity checks using PowerShell.
- Remove the temporary firewall rule after the practical.

Tools Used

- Windows 11
- Windows Defender Firewall
- Windows Defender Firewall with Advanced Security
- Windows PowerShell

Practical Details

Firewall Rule Configuration:

Parameter| Value
Rule Type| Port
Direction| Inbound
Protocol| TCP
Local Port| 23
Action| Block the connection
Profiles| Domain, Private, Public
Rule Name| Black Telnet Port 23

Commands Used

1. Test TCP connectivity

Test-NetConnection -ComputerName localhost -Port 23

2. Check for a listening service

Get-NetTCPConnection -LocalPort 23 -State Listen -ErrorAction SilentlyContinue

3. Start a temporary TCP listener

$listener = [System.Net.Sockets.TcpListener]::new([System.Net.IPAddress]::Any, 23)
$listener.Start()
Write-Host "TCP listener started on port 23"

4. Stop the temporary listener

$listener.Stop()
Write-Host "Temporary TCP listener stopped."

Observations

- The inbound TCP rule for port 23 was successfully created and its configuration was verified.
- The connectivity test returned "TcpTestSucceeded: False".
- No listening service was detected during the initial connectivity check.
- A connection test was not performed while the temporary listener was running.
- The temporary firewall rule was deleted after the practical.

Note: The failed localhost connection does not conclusively demonstrate that the firewall blocked the connection because no listening service was detected during the initial test.

Conclusion

This task provided practical experience with Windows Defender Firewall, inbound traffic filtering, TCP ports, and PowerShell network troubleshooting. It also demonstrated how to create, verify, and remove a temporary firewall rule.

Author

Dolly Panghate
