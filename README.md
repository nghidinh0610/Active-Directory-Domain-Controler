<h1>Active Directory Domain Controler</h1>

<h2>Description</h2>
Project consists of making an active directory for organizations to manage credential of users and network traffic. To be able to manage any data flow from external and internal through internet, organizations have to imply a main server (Active Directory) and let all organizations devices (Clients) using internet through that main server. It will help administrator be able to look at traffics and spot suspicious logs. The project also feature a powershell script creating 1000 users and an example for a device in this organization domain.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Oracle VM VirtualBox</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="9" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
This is the setting of the 2 VM we will create. DC will be the domain controler and CLIENT1 is just a VM to test log in information 
<br />
<img src="1" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
<img src="2" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
<br />
Setting up 2 network in DC, 1 NAT (to connect to your home internet) and 1 internal (for VM):  
<br/> (Additionally, change Shared Clipboard and Drag'n'Drop to Bidirectional to be able to copy stuff from your computer to VMs)
<br/><img src="5"height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/><img src="6"height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/><img src="3"height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Start the VM. When it ask for DVD, locate to Window Server 2019 ISO file: <br/>
<a href="https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019">You can download the Window Server 2019 ISO right here <a>
<br/><img src="7" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br/><img src="8" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Decline all service and create a password. Ideally Password1 for home lab and something else complicate in real environment:  <br/>
<img src="14" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log onto the VM. Rename your PC to DC. Go to network setting to setup IP  <br/>
Go to network setting on right down corner, click on the network setting, then choose "Change adapter options" <br/>
<img src="10" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now, go status ➡️ detail and look at IPv4 Address to rename them (1 is internal and 1 is home internet) <br/>
 The 10.0.*.* will be your home internet <br>
 The 1**.**.*.* will be your internal netowrk <br>
<img src="11" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After rename them, go to Internal and change its properties: <br/>
<img src="12" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
Go to Server Manager ➡️ Add roles and features ➡️ create an Active Directory, a DHCP Server and a DNS Serever<br/>
<img src="13" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
Go Server Manager ➡️ Tools ➡️ Active Diractory Users and Computers. <br>
Create an organization unit, name it ADMIN and assign your own admin account in there. <br>
Go to account properties memberof add enter the object name domain admin <br/>
<img src="15" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
<img src="17" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
<img src="18" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
 <br/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
 <br/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
 <br/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/><br>
 
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
