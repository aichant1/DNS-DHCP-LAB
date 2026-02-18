<h1>Windows Server DNS & DHCP Configuration</h1>


<h2>Description</h2>
This lab simulates a small enterprise network environment where a Windows Server is configured to provide DHCP and DNS services. It includes scope creation, IP reservation, internal name resolution testing, and DNS troubleshooting within a private 192.168.10.0/24 network.
<br />


<h2>Environments Used</h2>

- <b>Windows Server (DC01)
- Windows 10/11 Client (CLIENT01)
- VMware Fusion
- Private IPv4 network (192.168.10.0/24)
- Server Manager
- DHCP Management Console
- DNS Management Console
- Command Prompt (ipconfig, nslookup, ping)</b>

<h2>Key Tasks Performed</h2>

Installed and configured the DHCP Server role on Windows Server

Created and activated a DHCP scope (192.168.10.100–192.168.10.200)

Configured DHCP options including default gateway and DNS server

Created a DHCP reservation to assign a consistent IP address to a client device

Verified dynamic IP assignment using ipconfig /release and ipconfig /renew

Configured and verified a DNS forward lookup zone (lab.local)

Tested internal name resolution using ping and nslookup

Simulated a DNS misconfiguration and performed troubleshooting to restore connectivity

<h2>Skills Demonstrated </h2>

- <b>DHCP scope creation and activation
- DHCP reservation configuration (MAC-to-IP binding)
- Static IP configuration on Windows Server
- DNS forward lookup zone configuration
- Internal name resolution testing (ping, nslookup)
- DNS troubleshooting and cache flushing
- Understanding of IP addressing and subnetting
- Client/server communication flow analysis
- Basic network topology documentation <b>

<h2>Network Diagram</h2>  
<p align="center">
<img width="1024" height="768" alt="DNSDHCP Diagram" src="https://github.com/user-attachments/assets/6e475db6-7479-4880-af4f-a1ead262b325" />


<h2>Lab walk-through:</h2>
Coming Soon

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
