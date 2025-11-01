<h1>IP Configuration Reset Tool</h1>
<p align="center">
<img src="https://kruptos2.co.uk/blog/wp-content/uploads/2020/04/ip-address.jpg" alt="How to Hide Your IP Address: The ultimate step-by-step guide - Kruptos  Security Blog"/>
</p>  

This repository displays a useful PowerShell script you can run to reset and fix network configurations and network connectivity issues on your computer. Issues such as DNS, IP cache, or network adapter misconfigurations will be addressed by this tool.  

***Real World Use:***
When a user reports "No Internet Access" or "DNS Not Resolving", you can run this script and use it as a tool to reset and refresh the network stack.

***Detailed Breakdown of What the Script Will Do***  
Your PowerShell Script will use these main commands:

`ipconfig /release` - releases the current IP address assigned to your computer.  
`ipconfig /flushdns` - refreshes the DNS cache and clears stored DNS records.  
`netsh winsock reset` - reset Windows network sockets that are corrupted.  
`netsh int ip reset` - resets TCP/IP stack to its default configuration.  
`ipconifg /renew` - requests and assigns a new IP address from the DHCP server to your computer.  
`ipconfig /all` - displays the network adapter details such as IP, Default Gateway, DNS, etc.   

***How to Run It***  

1.) Save it as:   
`ipconfigresettool.ps1`   
2.) Run **PowerShell** as an **Administrator**   
3.) Navigate to the folder and execute the file by right-clicking and selecting "Run in PowerShell":  
```bash
.\ipconfigresettool.ps1
```
4.) Type `Y` to confirm.   

♻️<ins>***IP Configuration Reset Tool***<ins>♻️
```bash
<#
.SYNOPSIS
IP Configuration Reset Tool

.DESCRIPTION
This PowerShell script resets the network adapter, clears DNS cache, renews the IP address,
and resets Winsock and TCP/IP settings to restore network connectivity.

.AUTHOR
Stephen Langley
#>

Write-Host "============================================" -ForegroundColor Cyan
Write-Host "        IP CONFIGURATION RESET TOOL" -ForegroundColor Green
Write-Host "============================================" -ForegroundColor Cyan
Write-Host ""

# Confirm before starting
$Confirm = Read-Host "Do you want to reset your network configuration? (Y/N)"
if ($Confirm -ne "Y") {
    Write-Host "Operation canceled." -ForegroundColor Yellow
    exit
}

# Step 1: Release current IP configuration
Write-Host "`nReleasing current IP configuration..." -ForegroundColor Yellow
ipconfig /release
Start-Sleep -Seconds 2

# Step 2: Flush DNS cache
Write-Host "`nFlushing DNS resolver cache..." -ForegroundColor Yellow
ipconfig /flushdns
Start-Sleep -Seconds 2

# Step 3: Reset Winsock catalog
Write-Host "`nResetting Winsock catalog..." -ForegroundColor Yellow
netsh winsock reset
Start-Sleep -Seconds 2

# Step 4: Reset TCP/IP stack
Write-Host "`nResetting TCP/IP stack..." -ForegroundColor Yellow
netsh int ip reset
Start-Sleep -Seconds 2

# Step 5: Renew IP configuration
Write-Host "`nRenewing IP address..." -ForegroundColor Yellow
ipconfig /renew
Start-Sleep -Seconds 2

# Step 6: Display new IP configuration
Write-Host "`nDisplaying current network configuration..." -ForegroundColor Cyan
ipconfig /all

# Completion message
Write-Host "`nNetwork reset complete! A system restart may be required for all changes to take effect." -ForegroundColor Green
``` 
