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

- Setup Resources in Azure 
- Ensure Connectivity between the client and Domain Controller 
- Install Active Directory 
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First create a Resource Group.     
</p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Next create a Virtual Network and Subnet.
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>Then create the Domain Controller VM(Windows Server 2022) named "DC-1.
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 Click inside the box underneath of Licensing
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
Proceed to Create + Review  
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
Then you will create the Clinet VM (Windows 10) named "Client-1. Following the same steps as you did for DC-1 and click on Networking Tab, then choose most recent Virtual Network, next click Review + Create
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Finally you will Set Domain Controller's NIC Private IP address to be static. Go to Vitural Machine tab, click on Newtworking, click on dc-156, then click on IP configurations, click on link below "Search IP configurations", change Assignment form Dynamic to Static, then click save

 
<h2>Ensure Connectivity between the client and Domain Controller </h2> 
 
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Login to Client-1 DC-1 and ping DC-1s IP address with ping -t (perpetual ping). 
  1. Click on Client-1 
  2. Copy Public IP address 
  3. Open Remote Desktop Connection "using correct login/password"
  4. Go back to Virutal Machines 
  5. Click DC-1
  6. Copy Private IP address 
  7. Return back to Remote Desktop Connection 
  8. Go to start and open Command Prompt 
  9. Enter -t and paste Private IP address and then press enter
  10. Go back to DC-1
  11. Open another Remote Desktop Connection 

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Login to the Domain Controller and Enable ICMPv4 on the local windows Firewall 

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Logon to the windows VM and sure it can ping the Domain Controller 

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Check back CLient-1 to see the ping succeed

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>



<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Installl Active Directory </h2>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
<h2>Create an Admin and Normal User Account in AD</h2>







<h2>Join Client-1 to your domain (mydomain.com)</h2>
