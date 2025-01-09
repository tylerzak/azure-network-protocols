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
First, I created a resource group, a windows 10 virtual machine, and a linux virtual machine.
</p>
<br />

<p>
<img src="https://i.gyazo.com/e541b033f5b78dfdec6a297e9391b1fa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After confirming both virtual machines are on the same network and everything is setup correctly, I started the windows virtual machine through remote desktop connection and observed all of the ICMP traffic using WireShark and the ping command.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After that, I created a firewall (network security group) on azure to block the incoming traffic to observe what happens when pinging. As you can see, the request keeps timing out due to the rule that was created.
</p>
<br />
