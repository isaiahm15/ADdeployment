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

<p> Navigate to the Windows client VM, access its network interface settings, and customize the DNS server to the private IP address of the virtual server client.<br/>
<img src="https://github.com/user-attachments/assets/b416c88a-7a65-4805-96f7-7797aea7adf5" height="80%" width="100%" alt="Disk Sanitization Steps"/>
<br/>

<h2 align="center">Active Directory Installation & Setup</h2>

<p> Install ADDS (Active Directory Domain Services) in Server Manager from your virtual server.<br/>
<img src="https://github.com/user-attachments/assets/f108603f-462b-4a5e-bb7f-84ceba75cea8" height="80%" width="100%" alt="Disk Sanitization Steps"/>
<br/>

<p> Once ADDS is installed, click on "Promote this server to a domain controller".<br/>
<img src="https://github.com/user-attachments/assets/5c8c3099-fb5c-47f6-b793-23d27ded48ea" height="80%" width="100%" alt="Disk Sanitization Steps"/>
<br/>


<p align="center"> Add a new forest domain and create a password for the DSRM.
<br><i>Settings and options after this were left at their default values. You can proceed to the installation page and finalize the DC setup.</i></br>
<br>
<img src="https://github.com/user-attachments/assets/98248b03-c790-4241-8304-718f3aced9b8" height="100%" width="49.93%">
<img src="https://github.com/user-attachments/assets/6e46f8e3-d71d-4d94-83f4-59f41e1c1e62" height="100%" width="49.56%">

</p></br>

<p> Take a moment to restart both VMs to ensure Active Directory is in place.
<br/>
<img src="https://github.com/user-attachments/assets/ec465951-b745-4036-971a-2e611669f55a" height="80%" width="100%"/>
<br/>

<h2 align="center">Adding Windows 10 client to Active Directory</h2>

<p align="center"> Log into the Windows 10 client and right-click the Windows icon at the bottom left on the desktop, then click on System.
<br><i>Once the System settings opens, click on "Rename this PC (advanced)"</i></br>
<br>
<img align="center" src="https://github.com/user-attachments/assets/db77a348-647b-4ae3-8b01-0a754bed0d58" height="100%" width="35%">
<img align="center" src="https://github.com/user-attachments/assets/c1968ffc-fb4c-44ef-bf29-15f76746af8d" height="100%" width="58%">

</p></br>

<p align="center"> In System Properties, click on "Change" and then "Domain"
<br><i>(Right Image) Here, you should enter the forest domain you created earlier.</i></br>

<br>
<img align="center" src="https://github.com/user-attachments/assets/d41d9228-ad96-4122-9fe4-7035ea23a93a" height="100%" width="42.85%">
<img align="center" src="https://github.com/user-attachments/assets/12dee7b5-9654-4160-a0b4-1d3ac4e388fd" height="100%" width="43%">

</p></br>

<p align="center"> Your Windows client is now connected to the Active Directory.
<br><i>Make sure to have your domain client login information, you will need to authorize this domain change!</i></br>

<br>
<img align="center" src="https://github.com/user-attachments/assets/a66a2f63-fa7a-4331-bcea-0090e1fefce7" height="100%" width="42.85%">
<img align="center" src="https://github.com/user-attachments/assets/27ed838a-6b52-4a25-a30e-55d2308c5626" height="100%" width="53.25%">

</p></br>

<p>Use your domain client to launch Active Directory Users & Computers. Confirm that your added member client exists within the database.<br/>
 <br><i>This will be located in the "Computers" folder within your domain.</i></br>
<img src="https://github.com/user-attachments/assets/927d9c7e-6010-4600-b126-626d18c22277" height="80%" width="100%"/>
<br/>

<p>Once you're all set up, you can optionally create OUs (Organizational Units) to sort different departments from each other within your domain directory. Some typical uses for these are when you create domain groups and users, where you can then begin to configure a variety of permissions within each group and provision access among them.</p>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
