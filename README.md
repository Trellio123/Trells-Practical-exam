<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create 2 Virtual Machine using Azure
- Install Active Directory on One Virtual Machine
- Create Admin and User Account in Active Directory
- Join the domain using the other Virtual Machine
- Configue Remote Desktop for non-administrative users on VM 2
- Create addintional users and log into VM 2 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/IymFWZG.png"/>
</p>
<p>
First create 2 Virtual Machines using Windows 2022 Datacenter.
For this project I will refer to them as VM-1 and VM-2
Also set VM-2 DNS settings to VM-1 private IP Address
</p>
<br />

<p>
<img src="https://imgur.com/PUbNuYb.png"/>
</p>
<p>
Log into VM-1 and download Active Directory Domain Services
</p>
<p>
  <img src="https://imgur.com/3F844y3.png"/>
</p>
<p>
  On the top right click the flag and promote server to domain controller.
  After that click add forest as mydomain.com and restart VM as mydomain.com/(whatever you named your VM-1)
</p>
<br />

<p>
<img src="https://imgur.com/F6KnDQz.png"/>
</p>
<p>
In Active Directory Users and Computers ,create 2 Organizational Units called "_EMPLOYEES" and "Admins"
Create an employee (in the employee folder) with a name, add it to "Domain Admins" and remember the login information.
Log out of VM and log back in using the employee login info.
</p>
<br>
<p>
<img src="https://imgur.com/LEYTa4S.png" />
</p>
<p>
Login to VM-2, go to about pc settings> rename PC> Change domain> use the employee login, and let the VM-2 restart
</p>
<br />
<br>
<p>
  <img src="https://imgur.com/qCFBa22.png" />
</p>
<p>
  Log back into VM-1 as the domain controller and verify that VM-2 is in the Computer folder
</p>
<br/>
<br>
<p>
  <img src="https://imgur.com/tjMgWom.png" />
</p>
<p>
  Log into VM-2 using your mydomain.com\ credentials, open system properties, click remote desktop, allow domain users access to remote desktop.
</p>

