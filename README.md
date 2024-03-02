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

- Create Domain Controller VM
- Create Client 1 VM
- Install Active Directory Domain Services
- Add OUs, Admin Account, multiple user employee accounts

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
Login to DC-1 and install Active Directory Domain Services
Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
Restart and then log back into DC-1 as user: mydomain.com\labuser

</p>


<p>
<img src="https://imgur.com/Q04ldYU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
reate an Admin and Normal User Account in AD
In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”
Create a new OU named “_ADMINS”

</p>
<br />



<p>
<img src="https://imgur.com/bPdC8JE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”
Right click on mydomain.com -> new -> user
</p>
<br />



<p>
<img src="https://imgur.com/4gsVqai.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Add jane_admin to the “Domain Admins” Security Group
Log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\jane_admin”
User jane_admin as your admin account from now on
Right click on jane doe -> properties -> member of -> add -> type in domain admins -> find. Then add her in. 
</p>
<br />



<p>
<img src="https://imgur.com/Z4UsZMN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Join Client-1 to your domain (mydomain.com)
From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address
From the Azure Portal, restart Client-1

</p>
<br />



<p>
<img src="https://imgur.com/24qYJAX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain (computer will restart)
</p>
<br />



<p>
<img src="https://imgur.com/v6Nws39.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into Client-1 as mydomain.com\jane_admin and open system properties
Click “Remote Desktop”

</p>
<br />



<p>
<img src="https://imgur.com/s5CJtQA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Allow “domain users” access to remote desktop
You can now log into Client-1 as a normal, non-administrative user now
Normally you’d want to do this with Group Policy that allows you to change MANY systems at once 

</p>
<br />


<p>
<img src="https://imgur.com/vVrhhgd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a bunch of additional users and attempt to log into client-1 with one of the users
Login to DC-1 as jane_admin
Open PowerShell_ise as an administrator
Create a new File and paste the contents of the script into it (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)

</p>
<br />



<p>
<img src="https://imgur.com/BjNVEcG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Run the script (hit the play button) and observe the accounts being created



</p>
<br />



<p>
<img src="https://imgur.com/sFzAiip.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> Image of what the script is doing while creating accounts



</p>
<br />


<p>
<img src="https://imgur.com/J1oHPgE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> Head to Active Directory Uses and Comptuers, select an account you want to login to and save the username. 



</p>
<br />


<p>
<img src="https://imgur.com/IiEmpE5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> attempt to log into Client-1 with one of the accounts (take note of the password in the script)


</p>
<br />




