<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Setting up our resources in Azure
- Observing ICMP traffic
- Observing SSH traffic
- Observing DHCP traffic
- Observing DNS traffic
- Observing RDP traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/XsehKpJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Creating our resources:

Create a Resource Group in Azure

- Create a Windows 10 Virtual Machine (VM). While creating the VM, select the previously created Resource Group

- Create a Linux (Ubuntu) VM. While create the VM, select the previously created Resource Group and Vnet
</p>
<br />

<p>
<img src="https://i.imgur.com/lVbYDWI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observe the Virtual Network we created through Network Watcher in Azure.
</p>
<br />

<p>
<img src="https://i.imgur.com/N0mDYv7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Use Remote Desktop to connect to your Windows 10 Virtual Machine.
  
Within the Virtual Machine, Install Wireshark.

</p>
<br />

<p>
<img src="https://i.imgur.com/XHTz6rR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing ICMP Traffic: 

Open Wireshark and filter for ICMP traffic only.

Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM. Observe ping requests and replies within WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/eK3Afxe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing ICMP Traffic Continued: 
  
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/VUCXXFM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing ICMP Traffic Continued:

Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
</p>
<br />

<p>
<img src="https://i.imgur.com/yYlszIb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing ICMP Traffic Continued: 
  
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
  
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
</p>
<br />

<p>
<img src="https://i.imgur.com/rP20pHD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing ICMP Traffic Continued: 
  
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using

Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
Stop the ping activity
</p>
<br />


<p>
<img src="https://i.imgur.com/ImELEav.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing SSH Traffic: 
  
Back in Wireshark, filter for SSH traffic only. From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)

Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark

Exit the SSH connection by typing ‘exit’ and pressing [Enter]
</p>
<br />

<p>
<img src="https://i.imgur.com/ELs1efR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing DHCP Traffic: 

Back in Wireshark, filter for DHCP traffic only. 
  
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
Observe the DHCP traffic appearing in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/9s3yy81.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing DNS Traffic: 

Back in Wireshark, filter for DNS traffic only.

From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
Observe the DNS traffic being show in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/oD9tvJZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing RDP Traffic: 

Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)

Observe the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming?

because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted

</p>
<br />
