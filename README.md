<h1 align="center">Active Directory Home Lab

<a href="https://upload.wikimedia.org/wikipedia/commons/f/fa/Microsoft_Azure.svg" target="blank"><img align="middle" src="https://upload.wikimedia.org/wikipedia/commons/f/fa/Microsoft_Azure.svg" alt="isaiahmurphy" height="200" width="200" /></a>
<a href="https://github.com/user-attachments/assets/58f5815e-7a62-46cb-8aa6-e12bb01f6ccc" target="blank"><img align="middle" src="https://github.com/user-attachments/assets/58f5815e-7a62-46cb-8aa6-e12bb01f6ccc" alt="gmail" height="400" width="400" /></a>
</h1>

This lab guides you through how to deploy AD (Active Directory) using a virtual windows server and operating system through Azure, and how you can then connect clients to it. AD will provide you the means to organize and manage users or devices connected to its network. Some practical examples include user login management, creating separate domain groups by department for instance, and provisioning configurable access/permission levels for them.
<br/>


<h2 align="center">Databases & Programs Used</h2>
<p align="center">
<b>Azure</b>
 <p align="center">
<b>Server Manager</b>
<p align="center">
<b>Active Directory</b>

<h2 align="center">Environments Used </h2>
<p align="center">
<b>Windows 10 Enterprise</b> (22H2)

<h2 align="center">Deploy Windows Virtual Server & OS</h2>

<p align="center">
Configure and finalize your virtual server image within Azure. For this case, we used Windows Server 2022 Datacenter: Azure Edition.<br/>
<img src="https://github.com/user-attachments/assets/1fd262c5-8051-4d2a-ae37-1754bcad15cd" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 
<p align="center"><i>
Note: Be sure to direct your Windows OS VM to the same virtual network as your server VM!</i><br/>
<img src="https://github.com/user-attachments/assets/dca4db4a-c69c-4e04-b480-5ade8ce31e4a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p align="center"> Configure and finalize your virtual OS. 

<p align="center"><i>(Notice no virtual network was created here, since we're using the one created by the virtual server and don't need another.)</i><br/>
<img src="https://github.com/user-attachments/assets/9bcf9d71-3213-4556-a14e-62121b533727" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 
<h2 align="center">Installing Active Directory</h2>
<p align="center"> Install ADDS (Active Directory Domain Services) in Server Manager from your virtual server.<br/>
<img src="https://github.com/user-attachments/assets/e8ca9648-a0f2-412e-92a3-d8d513c28be4" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2 align="center">Installing the domain server</h2>
<p align="center">
 Click on the flag icon in the top right and promote the server to a domain controller. <br/>
<img src="https://github.com/user-attachments/assets/030697fe-f7ae-40a4-89ad-93e84f83e7ff" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p align="center"> Create or specify domain name. For this lab, we added a new forest. Click through the following fields and finalize the controller installation!<br/>
<img src="https://github.com/user-attachments/assets/64b6f2fb-390e-4969-8b5d-5200f4ad9fac" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p align="center"> Launch Active Directory to confirm proper installation.<br/>
<p align="center">
 <i>(We optionally created folders (Organizational Units) to organize clients, administrators, or groups.)</i>
<img src="https://github.com/user-attachments/assets/76f4ec07-4828-4e1f-b4ce-3432b867314e" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p align="center"> Switch to virtual Windows OS client and make it a member of your newly created forest domain.
 
 <p align="center"> <i>Right click Windows icon > System > Computer Name > Change > Member Of, Domain:</i>
 <br/>
<img src="https://github.com/user-attachments/assets/1ad058bf-e16c-4128-8c36-c7dac316ec45" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p align="center"> Return to virtual server client, launch Active Directory, confirm your added member client exists within the database.<br/>
<img src="https://github.com/user-attachments/assets/14b67382-c8bf-45a3-8d8c-23c1c6ec15b9" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
