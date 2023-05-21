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

Click Next on Installation Type 

<img src="https://i.imgur.com/F1wI1bO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click Next again

<img src="https://i.imgur.com/Mo8L3n1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Verify that your Domain (Windows Server 2022 Database) is chosen and click Next

<img src="https://i.imgur.com/k0TskiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Check Active Directory Domain Service Box and click Next

<img src="https://i.imgur.com/uRRNOLv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Continue to click Next until you reach the Install Option and click Install 

<img src="https://i.imgur.com/36UeuLs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click Close

<img src="https://i.imgur.com/OOgOXr8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on the Yellow tab and then Click on Promote this server to a domain controller 

<img src="https://i.imgur.com/3jt7OQf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Check the box Add a new forest and then enter create a name inside the Root domain name

<img src="https://i.imgur.com/7FVjINn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Create a Password and Click Next 

<img src="https://i.imgur.com/1AmbSOW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Continue to click the Next tab and then click the Install tab

<img src=" https://i.imgur.com/VQmmSnx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go back to Virtual Machine (Domain Server)

<img src="https://i.imgur.com/LjyOmlC.png " height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on Use a different account, then type in your domain name, next to your domain name attach \labuser, type in your password and then hit OK

<img src="https://i.imgur.com/ApByIc7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Open Domain server and type in Active Directory and choose Active Directory Users and Computers

<img src="https://i.imgur.com/nM0Z2Eo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Right click on your server (mydomain.com), go to New and then choose Organizational Unit

<img src="https://i.imgur.com/E4yqQAk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Name your file

<img src=" https://i.imgur.com/kaTdF64.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on _ADMIN, then scroll down to New, and then User, to create another Admin file

<img src="https://i.imgur.com/PrFPDnm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Type in the correct information and click Next

<img src="https://i.imgur.com/xkSdRtW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Making User into Admin:
Rght click on name, scroll to Properties and click it

<img src="https://i.imgur.com/7Et2f3C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Select Member tab and hit Ok.

<img src="https://i.imgur.com/ndKbNAS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click Add tab

<img src="https://i.imgur.com/FGg74oF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Type in domain and click Check Names to verify which Group the Admin will go into

<img src="https://i.imgur.com/4w3aCBI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Choose Domain Admins and then hit OK

<img src="https://i.imgur.com/ONdePdi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Hit OK

<img src="https://i.imgur.com/lDxMK1y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click Apply and then hit OK

<img src="https://i.imgur.com/Eq9iUPC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Logoff and then sign back with different account. Login as mydomain.com\jane_admin

<img src="https://i.imgur.com/TrHOJUB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go to Start Menu and type in Command Prompt, then type “whoami”, to verify you are in the correct Desktop

<img src="https://i.imgur.com/IIJOX7j.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>



<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>





</p>
<br />
<h2>Create an Admin and Normal User Account in AD</h2>







<h2>Join Client-1 to your domain (mydomain.com)</h2>
