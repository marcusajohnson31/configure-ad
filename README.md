<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://imgur.com/DUjRlxp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Setup Resources in Azure
Create the Domain Controller VM (Windows Server 2022) named “DC-1”
Take note of the Resource Group and Virtual Network (Vnet) that get created at this time
Set Domain Controller’s NIC Private IP address to be static
Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created in Step 1.a
Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher

</p>
<br />

<p>
<img src="https://imgur.com/4gsVqai.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ensure Connectivity between the client and Domain Controller
Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping  <ip address> 
</p>
<br />

<p>
<img src="https://imgur.com/6FLXQIP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall
Check back at Client-1 to see the ping succeed

</p>
<br />


<p>
<img src="https://imgur.com/8KOgyXg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The ping has succeeded 
</p>
<br />

<h2>Video Demonstration</h2>

- ### [YouTube: How to Install Active Directory Domain Services ](https://www.youtube.com/watch?v=6ig5vTzME20)



<p>
<img src="https://imgur.com/4gsVqai.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ensure Connectivity between the client and Domain Controller
Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping  <ip address> 
</p>
<br />



<p>
<img src="https://imgur.com/4gsVqai.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ensure Connectivity between the client and Domain Controller
Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping  <ip address> 
</p>
<br />



<p>
<img src="https://imgur.com/4gsVqai.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ensure Connectivity between the client and Domain Controller
Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping  <ip address> 
</p>
<br />



<p>
<img src="https://imgur.com/4gsVqai.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ensure Connectivity between the client and Domain Controller
Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping  <ip address> 
</p>
<br />
