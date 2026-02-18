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

Created Organizational Units (IT, Finance, HR) and security groups for each department

Built a CSV file to simulate HR onboarding data and imported into Powershell

Generated usernames automatically (first initial + last name) and secure temporary passwords

Automated creating Active Directory user accounts, assigned them to the correct OUs based on departments and added them to department-based security groups

Exported a provisioning report to CSV

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


<h2>Powershell Script:</h2>

    # Loads the Active Directory PowerShell commands
    Import-Module ActiveDirectory

    # Reads the HR spreadsheet (CSV) into a list of user records
    $users = Import-Csv "C:\HR-NewHires.csv"

    # This will store results so we can export a report at the end
    $report = @()

    # Loop through each row in the CSV (each employee)
    foreach ($user in $users) {

    # Build a username like: jreed (first initial + last name)
    $username = ($user.FirstName.Substring(0,1) + $user.LastName).ToLower()

    # Generate a random temporary password (12 chars, includes 2 special chars)
    Add-Type -AssemblyName System.Web
    $password = [System.Web.Security.Membership]::GeneratePassword(12,2)

    # Convert the password to a secure format required by New-ADUser
    $securePassword = ConvertTo-SecureString $password -AsPlainText -Force

    # Choose which OU the user goes into based on Department
    # Example: OU=IT,DC=nylab,DC=local
    $ouPath = "OU=$($user.Department),REPLACE_WITH_YOUR_DOMAIN_DN"

    # Create the user in Active Directory
    New-ADUser `
        -Name "$($user.FirstName) $($user.LastName)" `
        -GivenName $user.FirstName `
        -Surname $user.LastName `
        -SamAccountName $username `
        -UserPrincipalName "$username@REPLACE_WITH_YOUR_DOMAIN_DNS" `
        -Path $ouPath `
        -AccountPassword $securePassword `
        -Enabled $true `
        -ChangePasswordAtLogon $true `
        -Title $user.Title `
        -Department $user.Department

    # Add the user to the correct department security group (like IT-Users)
    Add-ADGroupMember -Identity "$($user.Department)-Users" -Members $username

    # Add this user to our report object (so we can export results)
    $report += [PSCustomObject]@{
        Name = "$($user.FirstName) $($user.LastName)"
        Username = $username
        Department = $user.Department
        TemporaryPassword = $password
      }

    }
    # Export the results to a CSV so we have proof / documentation
    $report | Export-Csv "C:\ProvisioningReport.csv" -NoTypeInformation
    Write-Host "Provisioning complete. Report saved to C:\ProvisioningReport.csv"

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
