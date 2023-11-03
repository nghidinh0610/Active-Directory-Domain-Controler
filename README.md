<h1>Active Directory Domain Controler</h1>

 ### [Tutorial Source](https://www.youtube.com/watch?v=MHsI8hJmggI)

<h2>Description</h2>
Project consists of making an active directory for organizations to manage credential of users and network traffic. Consist of a Powershell script to create 1000 users and another VM to test log in.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Oracle VM VirtualBox</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/S3ZueSd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
This is the setting of the 2 VM we will create. DC will be the domain controler and CLIENT1 is just a VM to test log in information 
<br />
<br />
Setting up 2 network in DC, 1 NAT (to connect to your home internet) and 1 internal (for VM):  
<br/> (Additionally, change Shared Clipboard and Drag'n'Drop to Bidirectional to be able to copy stuff from your computer to VMs)
<br/><img src=""height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/><img src=""height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Start the VM. WHen it ask for DVD, locate to Window Server 2019 ISO file: <br/>
<a href="https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019">You can download the Window Server 2019 ISO right here <a>
<br/><img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br/><img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Decline all service and create a password. Ideally Password1 for home lab and something else complicate in real environment:  <br/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log onto the VM. Go to network setting to setup IP  <br/>
Go to network setting on right down corner, click on the network setting, then choose "Change adapter options"
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
