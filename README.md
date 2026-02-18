<h1>Windows Server DNS & DHCP Configuration</h1>


<h2>Description</h2>
This lab simulates a small enterprise network environment where a Windows Server is configured to provide DHCP and DNS services. It includes scope creation, IP reservation, internal name resolution testing, and DNS troubleshooting within a private 192.168.10.0/24 network.
<br />


<h2>Environments Used</h2>

- <b>Windows Server (DC01)
- Windows 10/11 Client (CLIENT01)
- VMware
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

<p align="center">
Created department-based security groups (IT-Users, Finance-Users, HR-Users).
These groups simulate role-based access control (RBAC) used in enterprise environments to assign permissions based on department. <br/> <br/>
<img width="80%" height="80%" alt="Screenshot 2026-02-13 at 11 17 57 PM" src="https://github.com/user-attachments/assets/ffff51ec-2eb7-4591-9487-c8a885a26752" />
<br />
<br/>
Created a CSV file to simulate HR onboarding data. <br/> <br/>
<img width="80%" height="80%" alt="Screenshot 2026-02-13 at 11 20 56 PM" src="https://github.com/user-attachments/assets/1b13a076-f2aa-4fba-8585-a2537ba64e26" />
<br />
<br />
Developed a PowerShell script to automate Active Directory user provisioning. <br/> <br/>
<img width="80%" height="80%" alt="Screenshot 2026-02-14 at 12 15 16 AM" src="https://github.com/user-attachments/assets/e3b77b07-36a4-43cf-b76b-81429d04e007" />
<br />
<br />
Executed the PowerShell provisioning script (Provision-NewHires.ps1) from the C:\ directory.  <br/> <br/>
<img width="80%" height="80%" alt="Screenshot 2026-02-16 at 10 23 18 PM" src="https://github.com/user-attachments/assets/573f918a-8dfb-4396-bf20-fd5a3690515a" />
<br />
<br />
Verified that the script exported a structured CSV report containing. <br/> <br/>
<img width="80%" height="80%" alt="Screenshot 2026-02-16 at 11 37 46 PM" src="https://github.com/user-attachments/assets/4c203c65-2645-4c02-92f4-bccc93de07ff" />


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
