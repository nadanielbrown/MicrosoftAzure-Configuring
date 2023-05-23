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

- Setup Resources in Azure 
- Ensure Connectivity between the client and Domain Controller 
- Install Active Directory 
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)

<h2>Deployment and Configuration Steps</h2>

First Create a Resource Group.     

<img src="https://i.imgur.com/pO6EEPi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/qimxeZD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on Create and then select the Azure virtual machine tab

<img src="https://i.imgur.com/RdnP1Uf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/3EV3HxM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
 
Create New Resource Group

<img src="https://i.imgur.com/KTwWdIa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Type in DC-1 for Virtual machine name
Select the Domain Controller VM(Windows Server 2022 Datacenter: Azure Edition) for "Image"

<img src="https://i.imgur.com/PyKrztk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Create User name and Password

 <img src="https://i.imgur.com/D3s9WpS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Then you will create the Clinet VM (Windows 10) named "Client-1. Following the same steps as you did for DC-1 and click on Networking Tab, then choose most recent Virtual Network, next click Review + Create
  
 <img src="https://i.imgur.com/RdnP1Uf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/3EV3HxM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
 
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

</p>
<br />
<h2>Create an Admin and Normal User Account in AD</h2>

<h2>Join Client-1 to your domain (mydomain.com)</h2>

Login to CLient-1 as the original local admin (labuser) and join it to the domain (computer will restart)

<img src="https://i.imgur.com/k8Ke2mL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Copy Client-1 IP address 

<img src="https://i.imgur.com/mHJVYg3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go to Remote Desktop in Start Menu and click it

<img src="https://i.imgur.com/0JLsm48.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

CLick add PC and then enter your name(labuser) and created password (what you chose)

<img src="https://i.imgur.com/4HEFokH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Right click and the Start Menu 

<img src="https://i.imgur.com/yEyu9P7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go to System

<img src="https://i.imgur.com/SSh0Kre.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on Rename this PC (advanced)

<img src="https://i.imgur.com/dOWeOVw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on Change

<img src="https://i.imgur.com/dnJm4uT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on Domain

<img src="https://i.imgur.com/m9I0WNV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Type in "domain.com" another box will open "Computer Name/Domain Changes" hit Ok

<img src="https://i.imgur.com/9B0Fc6X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Need to "Set DNS Server" inside the Azure portal
Go to Domain (wsDC01)

<img src="https://i.imgur.com/xw9Eu2b.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on Networking and copy the NIC Private IP

<img src="https://i.imgur.com/Te7WoYu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on Client-1

<img src="https://i.imgur.com/m9I0WNV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click Networking and then click win10-client-1598_z1

<img src="https://i.imgur.com/z1h1XdI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Then go to DNS server

<img src="https://i.imgur.com/1GOX5DU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Choose Custom and then enter IP Address, next hit Save. Make sure there are no spaces in front of your IP Address

<img src="https://i.imgur.com/UXKGw9r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/rkS5NK4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go back to Virtural Machine and click on CLient-1

<img src="https://i.imgur.com/QINsmAn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Hit Restart

<img src="https://i.imgur.com/ZIkSFJx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Open Remote Desktop and enter Client-1 Public IP address and hit Connect

<img src="https://i.imgur.com/2ElQ3Im.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Type in your password

<img src="https://i.imgur.com/I5EGu5N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Open Command Prompt
Type whoami, to verify user
Type hostname, to verify username
Type ipconfig/all, to verify DNS server

<img src="https://i.imgur.com/L5r2FRa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Right click on Start Menu and go to System

<img src="https://i.imgur.com/oWVCz2c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go to Rename this PC

<img src="https://imgur.com/a/VCL2TGP" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click Change

<img src="https://i.imgur.com/QqCBJ32.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Check the Domain box and type in "mydomain.com" and hit OK

<img src="https://i.imgur.com/mArbG8Q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Type in user name and password that was created earlier for Jane as an Admin user

<img src="https://i.imgur.com/o2beWIz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Hit Ok for the next screens that pop-up and then Click Restart

<img src="https://i.imgur.com/o2beWIz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ogMeVDS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Niopg0l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/KcZCYnA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go back to Remote Desktop and connect back in 

<img src="https://i.imgur.com/KkVKJR7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on More Choices

<img src="https://i.imgur.com/BGrGY0q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Type in "mydomain.com\jane_admin as "User" and type in your password that you used before

<img src="https://i.imgur.com/kp1CPcC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Next set up the system where all normal users will be able to log in Client-1

Right click on Start Menu and go to System

<img src="https://i.imgur.com/oWVCz2c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click "Remote desktop"

<img src="https://i.imgur.com/2FFTmcq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on "Select users that can remotely access this PC"

<img src="https://i.imgur.com/PeAeagJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click Add

<img src="https://i.imgur.com/DENPLfj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Type in "domain name" and hit Check Names, then hit OK

<img src="https://i.imgur.com/AnxdOUf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Hit Ok

<img src="https://i.imgur.com/AnxdOUf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Open Remote Desktop Connection and go back to Domain server 

<img src="https://i.imgur.com/R6wdyYA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go to Start Menu and Click Windows Administrative Tools, then Click on Active Directory Users and Computers

<img src="https://i.imgur.com/tK8lOk1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on "mydomain.com, next click on the folder "Users"

<img src="https://i.imgur.com/YW4uNpD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Double Click Domain Users

<img src="https://i.imgur.com/dKWuHBB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click Member tab and verify correct users

<img src="https://i.imgur.com/e7Ttpug.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Creating a bunch of additional users and attempt to log into Client-1 with one of the users

Open DC-1(jane_admin) Remote Desktop
Go to Start Menu and enter Command Portal and type in "whoamI" and then type in hostname, verify that your information is correct

<img src="https://i.imgur.com/XZjgvF0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go to Start Menu and type in "Windows PowerShell ISE", Right Click on Windows PowerShell ISE and select Run as Administrator 

<img src="https://i.imgur.com/QSL0Y0C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Open script link in a new browser

<img src="https://i.imgur.com/Evs4L0u.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Copy raw file 

<img src="https://i.imgur.com/xJ253M5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Return back to Windows PowerShell ISE and click New Script

<img src="https://i.imgur.com/Oq7KwxQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Paste the raw file

<img src="https://i.imgur.com/EJ4Hlcy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click Run 

<img src="https://i.imgur.com/yXobpSn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Go to Active Directory Users and Computers and right click _EMPLOYEES folder and select REFRESH

<img src="https://i.imgur.com/1BN6zRl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Click on a user name and right click and copy

<img src="https://i.imgur.com/IPzK36F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Next click on Account tab and copy user name logon name (ex: baba.judev)

<img src="https://i.imgur.com/Cl2nys3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Sign out of Client-1 and then Sign back in to Client-1

<img src="https://i.imgur.com/2EiULZg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/2yhEtYF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Type in user name mydomain.com\baba.judev

Inside of the Start Menu, go to Command Prompt and type "whoami" press Enter and then type "hostname" press Enter

<img src="https://i.imgur.com/KMrPJsI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</h1>!!!YOU HAVE SUCCESSFULLY COMPLETED!!!</h1>
On-premises Active Directory Deployed in the Cloud (Azure)
