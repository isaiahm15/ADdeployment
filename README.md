<h1 align="center">Active Directory: Deployment</h1>

<h1 align="center" a href="https://upload.wikimedia.org/wikipedia/commons/f/fa/Microsoft_Azure.svg" target="blank"><img align="middle" src="https://upload.wikimedia.org/wikipedia/commons/f/fa/Microsoft_Azure.svg" alt="isaiahmurphy" height="200" width="200" /></a>
<a href="https://github.com/user-attachments/assets/58f5815e-7a62-46cb-8aa6-e12bb01f6ccc" target="blank"><img align="middle" src="https://github.com/user-attachments/assets/58f5815e-7a62-46cb-8aa6-e12bb01f6ccc" alt="gmail" height="400" width="400" /></a>
</h1>

This lab guides you through how to deploy AD (Active Directory) using a virtual Windows server and operating system through Azure, and how you can then connect clients to it. AD will provide you with the means to organize and manage users or devices connected to its network. Some practical examples include user login management, creating separate domain groups by department, and provisioning configurable access/permission levels for them.
<br/>


<h2>Databases & Programs Used</h2>
<p>
 
- <b>Azure</b>

- <b>Server Manager</b>

- <b>Active Directory</b>

</p>

<h2>Environments Used </h2>
<p>
 
- <b>Windows 10 Enterprise</b> (22H2)

</p>

<h2>Step-by-Step Overview</h2>
<p>
 
- <b>Create dedicated resource group within Azure</b>

- <b>Configure and deploy virtual domain server client</b>

- <b>Configure and deploy virtual Windows 10 client</b>

- <b>Link both VMs to the same virtual network</b>

- <b>Change the domain server VM private IP address allocation to static</b>

- <b>Change the virtual Windows 10 client's DNS server to "custom" and set it to the domain server's static private IP address</b>

- <b>Install Active Directory Domain Service through the domain server client's Server Manager</b>

- <b>Promote the domain server to a domain controller</b>

- <b>Create a new forest domain (Restart Windows 10 VM)</b>

- <b>Add Windows 10 client to the domain controller's newly created Active Directory</b>

- <b>Return to the domain server client to observe and confirm the Windows 10 client exists within the Active Directory</b>

<h2 align="center">Creating Resources</h2>

</p>
Create a resource group within Azure. This will be used to store both virtual machines once they're created.
<br><img src="https://github.com/user-attachments/assets/a8f2c340-ec7a-4168-a111-8d9148e19f78" height="75%" width="100%" alt="Disk Sanitization Steps"/>
<br/>
</p>

<p align="center"> Configure and finalize your virtual server image within Azure. For this case, we used Windows Server 2022 Datacenter: Azure Edition.
 
<br>
<img src="https://github.com/user-attachments/assets/2fa936ce-2469-4409-9744-2639aef712b5" height="75%" width="95.55%">
<img src="https://github.com/user-attachments/assets/c117630d-ea5f-427d-8cd5-7a4c5e8f7176" height="100%" width="47%">
<img src="https://github.com/user-attachments/assets/1909c849-4d10-4216-99c2-eb8d4bbe4622" height="100%" width="48.08%">

</p></br>

<p align="center"> Create another VM using a Windows 10 OS image.
 
<br>
<img src="https://github.com/user-attachments/assets/06bec7c4-6296-4b10-abb4-4beaa178a8c0" height="75%" width="95.55%">
<img src="https://github.com/user-attachments/assets/bf99c05f-d248-408f-9a6b-e4075ab541fc" height="100%" width="47%">
<img src="https://github.com/user-attachments/assets/baa4adf6-48a4-4e02-8f91-79557b3f5a8e" height="100%" width="47.78%">

</p></br>
 
<h2 align="center">Configure Private IP Address & DNS Settings</h2>

<p> Return to Azure and set the virtual server's private IP address to static. <br>This will prepare the virtual Windows OS client to connect to Active Directory.<br/>
<img src="https://github.com/user-attachments/assets/729fd9df-a3f5-49ec-8f31-ac37e98a829a" height="75%" width="100%" alt="Disk Sanitization Steps"/>
<br/>

<p> Navigate to the Windows client VM, access network settings, and customize the DNS server to the private IP address of the virtual server client.<br/>
<img src="https://github.com/user-attachments/assets/b416c88a-7a65-4805-96f7-7797aea7adf5" height="80%" width="100%" alt="Disk Sanitization Steps"/>
<br/>

<h2>Installing Active Directory</h2>
<p> Install ADDS (Active Directory Domain Services) in Server Manager from your virtual server.<br/>
<img src="https://github.com/user-attachments/assets/e8ca9648-a0f2-412e-92a3-d8d513c28be4" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>Installing the domain server</h2>
<p>
 Click on the flag icon in the top right and promote the server to a domain controller. <br/>
<img src="https://github.com/user-attachments/assets/488d036b-2df8-4bc6-836e-4e58f6f7fc7d" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p> Create or specify a domain name. For this lab, we added a new forest. Click through the following fields and finalize the controller installation!<br/>
<img src="https://github.com/user-attachments/assets/64b6f2fb-390e-4969-8b5d-5200f4ad9fac" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p> Launch Active Directory to confirm proper installation.<br/>
<p>
 <i>(We optionally created folders (Organizational Units) to organize clients, administrators, or groups.)</i>
<img src="https://github.com/user-attachments/assets/76f4ec07-4828-4e1f-b4ce-3432b867314e" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p> Switch to the virtual Windows OS client and make it a member of your newly created forest domain.
 
 <p> <i>Right click Windows icon > System > Rename My Pc (advanced) > Computer Name > Change > Member Of, Domain:</i>
 <br/>
   <p><i>(You will need the sign-in information from your virtual server client to finalize this.)</i><br/>
<br />
<br />
<img src="https://github.com/user-attachments/assets/1ad058bf-e16c-4128-8c36-c7dac316ec45" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p> Return to the virtual server client, launch Active Directory, and confirm your added member client exists within the database.<br/>
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
