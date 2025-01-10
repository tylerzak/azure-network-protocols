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

- Create Virtual Machines
- Observe ICMP Traffic
- Configure a Firewall (Network Security Group)
- Observe SSH, DHCP, DNS, and RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.gyazo.com/12ebc665421d75076e5bbc1df9931c94.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.gyazo.com/a4d021ef7b93f320efbc2029eb944210.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.gyazo.com/fa1201a085a12bd543df669a529ec57c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First, I created a resource group, a Windows 10 virtual machine, and a Linux virtual machine on Azure.
</p>
<br />

<p>
<img src="https://i.gyazo.com/e541b033f5b78dfdec6a297e9391b1fa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.gyazo.com/7520919cc7d472f3d218f08497ee083e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After confirming that both virtual machines are on the same network and ensuring everything is set up correctly, I started the Windows virtual machine through Remote Desktop Connection. I then observed all ICMP traffic between the two virtual machines using Wireshark and the ping command on Windows PowerShell.
</p>
<br />

<p>
<img src="https://i.gyazo.com/76d48a6ad8975922be2afffa5b5b92e6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.gyazo.com/2c112cde1b8422bd2992ab3d70d99fa7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.gyazo.com/f0659314f7206e6b99bce2d495a4c207.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After creating an inbound security rule under the Linux virtual machine's network security group on Azure to block incoming ping traffic, I observed its effects. As expected, the requests timed out due to the rule I had implemented. Additionally, Wireshark was unable to capture any replies, further confirming the rule's effectiveness. Once the rule was deleted, traffic resumed as expected.
</p>
<br />

<p>
<img src="https://i.gyazo.com/ba56235e299416dce8b662fd0d5f7857.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I observed all SSH traffic after logging into the Linux virtual machine using the SSH command in Windows PowerShell and filtered it in Wireshark. Additionally, I performed a few tasks in PowerShell, such as creating a text file and executing several commands.
</p>
<br />

<p>
<img src="https://i.gyazo.com/cd8f32b45df4e5590622637723aec201.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.gyazo.com/34704c69643a795a0c32af7072786376.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I observed all DHCP traffic after creating a .bat file. After running the file in Windows PowerShell, I monitored the traffic in Wireshark, filtering it specifically for DHCP. The sequence displayed in Wireshark represents a typical DHCP lease cycle, where the client requests an IP address, receives an offer, confirms the offer, and later releases the IP address.
</p>
<br />

<p>
<img src="https://i.gyazo.com/8bdce5af630cfa5ba7f0c39a325a1583.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I observed all DNS traffic on Wireshark after executing the nslookup command in PowerShell. For this example, I used "disney". As you can see, the nslookup query for "disney.com" returned an IP address from a non-authoritative DNS server.
</p>
<br />
