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
`**netsh winsock reset**` - reset Windows network sockets that are corrupted.  
`netsh int ip reset` - resets TCP/IP stack to its default configuration.  
`ipconifg /renew` - requests and assigns a new IP address from the DHCP server to your computer.  
`ipconfig /all` - displays the network adapter details such as IP, Default Gateway, DNS, etc.   

***How to Run It***  

1.) Save it as:   
`ipconfigresettool.ps1`   
2.) Run **PowerShell** as an **Administrator**   
3.) Navigate to the folder and execute the file:  
```bash
.\ipconfigresettool.ps1
```
4.) Type `Y` to confirm.   
