<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Implementing a Help Desk Ticketing System using Microsoft Azure Virtual Machines</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- PHP Manager
- Rewrite Module
- PHP 7.3.8
- VC_redist.x86
- MySQL
- OsTicket
- HeidiSQL

<h2>Installation Steps</h2>

<p>


</p>
<p>
Create a virtual machine in Azure that runs Windows 10 and has 2-4 cores. Once it's intiated connect to it with remote desktop and enable IIS. Do this by clicking on the search bar and searching control panel then go to programs and then click Windows features on or off and enable Internet Information Serves and then enable CGI inisde of Application Development Features and Common HTTP Features also make sure IIS Management Console is enabled inside of WebManagement Tools. 
Let's go to portal.azure.com to open up a Resource group and name it RG-osTicket, place it in Region (US)East US, Security type Standard, Image Windows 10 Pro, version 22H2 x64 Gen2, Size Standard D4s v3 4vcpus, 16GiB memory, a username labusertd and a password labusertdAzure1$, and check box for licensing. Click Next Disks, then click Next Networking, then click Review and create. Onvce validation passes click create and allow deployment to process.  Now lets take a look at the resources we created. Take note of the Public and Private IP Addresses for vm-osTicket and the Resource group RG-osTicket. Take note of all of your virtual resources as well: VM, Network Security Group, Network, Interface and Disk.

</p>
<br />

![Azure ResourceGroup](https://github.com/TDCybersecurity/osTicket-Post-Installation-Setup/assets/142702123/8c08fe53-155f-4ab0-a0c0-8457486b5212)
![Azure2](https://github.com/TDCybersecurity/osTicket-Post-Installation-Setup/assets/142702123/3a0452a1-9057-4525-92d7-4a792d75cfdc)
![image](https://github.com/TDCybersecurity/osTicket-Post-Installation-Setup/assets/142702123/8efb65e2-f522-477b-a3f5-a33cba7c23e8)
![Take not of VMs](https://github.com/TDCybersecurity/osTicket-Post-Installation-Setup/assets/142702123/7171f16a-87b3-4c6b-8c86-a720f666971b)
![osTicket 5](https://github.com/TDCybersecurity/osTicket-Post-Installation-Setup/assets/142702123/15ca7b23-8588-4f39-9283-a6a0d5e773fb)

</p>

<p>
Now lets open vm-osTicket and make a Remote Desktop Connection, copy and paste the vm-osTicket Public IP Address,  press connect, and login using the other user option with user labusertd and password userlabtdAzure1$. After the VM opens change all Microsoft privacy settings to NO and press Accept, start without your data, do not bring over your data, continue and confirm.  You are done here. Note: virtual IPs change with each creation and you will have your own usernames and passwords
</p>
<br />


![osTicketRemote1](https://github.com/TDCybersecurity/osTicket-Post-Installation-Setup/assets/142702123/675bef10-ae13-4ae6-bc3f-6cc63c52754a)
![Remote2](https://github.com/TDCybersecurity/osTicket-Post-Installation-Setup/assets/142702123/ff83f789-7689-4d71-a245-6385f471baa1)
![VM Privacy](https://github.com/TDCybersecurity/osTicket-Post-Installation-Setup/assets/142702123/8c1b98fa-746e-481d-a12c-2f4e9b7c02a7)
![Remote3](https://github.com/TDCybersecurity/osTicket-Post-Installation-Setup/assets/142702123/5b323496-bbf4-4894-a46c-2a4a1ecc0569)

</p>
<p>
Install PHP Manager band be sure to click download anyway. then install the rewrite module and do the same. Use these links: <br />
   <a href= "https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view?usp=share_link"> PHP Manager </a>
  <br />
  <a href= "https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view?usp=share_link"> Rewrite Module </a>
</p>
<br />

<p>
<img src="https://i.imgur.com/7xgSxDS.png"/>
</p>
<p>
Create a folder in the C drive called PHP this is directory C:\PHP. Next install PHP 7.3.8 by using the link below: <br />
  <a href="https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view?usp=share_link"> PHP 7.3.8</a>
</p>
<br />

<p>
<img src="https://i.imgur.com/zfLe0GP.png"/>
</p>
<p>
This will download a ZIP file go to downloads in file explore right click on the folder and extract to C:\PHP
</p>
<br />

<p>
<img src="https://i.imgur.com/urpGkfs.png"/>
</p>
<p>
Install VC_Redist and MySQL. The links will be below. When the setup wizard for MySQL launches do a typial and standard setup. Then set the password to be password1. <br \>
<a href="https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view?usp=share_link"> VC </a> <br \>
<a href="https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link"> MySQL </a> 
</p>
<br />

<p>
<img src="https://i.imgur.com/RtJ3X2v.png"/>
</p>
<p>
Go to the Windows search bar and type in Internet Information Services to open its management window. Click on PHP manager and then register PHP with the directory shown in the above screen shot. After registering PHP reload IIS.
</p>
<br />

<p>
<img src="https://i.imgur.com/cfzo00u.png"/>
</p>
<p>
Use the installation file link to install OsTicket and extract the upload folder to c:\inetpub\wwwroot  and rename it to osTicket then reload IIS. Be sure to be running IIS as an administrator <br \>
<a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation File </a>
</p>
<br />

<p>
<img src="https://i.imgur.com/T85wCxZ.png"/>
</p>
<p>
If every step was done correctly then you should see this screen when you click browse 80 on IIS after going to the Default Website branch on the left of the IIS managaer. 
</p>
<br />

<p>
<img src="https://i.imgur.com/o5jn685.png"/>
</p>
<p>
Go to the PHP manager and click on enable extensions and enable the extensions listed below by scrolling to it, right clicking and clicking enable rule: <br \>
Enable: php_imap.dll
  <br \>
Enable: php_intl.dll
  <br \>
Enable: php_opcache.dll

  
</p>
<br />

<p>
<img src="https://i.imgur.com/MhYRVn5.png"/>
</p>
<p>
Go to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename the file ost-config.php then right click it go to properties and then security. Go to permissions disable its inheritence then add a principal and give everyone read/write permission.
</p>
<br />

<p>
<img src="https://i.imgur.com/tttew8D.png"/>
</p>
<p>
Install Heidi SQL and use root/password1 as the login and create a database called osTicket. Do this by right clicking unnamed then going to create new and then database.<br \>
<a href="https://docs.google.com/document/d/1WovrX2DaS9xkfaSr4LXyB4YnnWpXIgPCMMbbfgHmGVw/edit"> HeidiSQL </a>
  
</p>
<br />

<p>
<img src="https://i.imgur.com/VZ2KRmQ.png"/>
</p>
<p>
Go to OsTicket in your web browser continue the setup by adding in these texts for these fields: <br \>
  MySQL Database: osTicker<br />
  MySQL Username: root <br \>
  MySQL Password: password1
  <br \>
This should complete the installationa and prompt you to begin the cleanup process which is to delete C:\inetpub\wwwroot\osTicket\setup and to set permissions to Read only for C:\inetpub\wwwroot\osTicket\include\ost-config.php This concludes the setup demonstration for osTicket.
</p>
<br />





</p>
<p>

</p>
<br /># post-install-config
