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
<img src="" height="80%" width="80%" alt="9"/><br />
 
This is the setting of the 2 VM we will create. DC will be the domain controler and CLIENT1 is just a VM to test log in information 
<br />
<img src="" height="80%" width="80%" alt="1"/><br>
<img src="" height="80%" width="80%" alt="2"/><br>
<br />

Setting up 2 network in DC, 1 NAT (to connect to your home internet) and 1 internal (for VM):  
<br/> (Additionally, change Shared Clipboard and Drag'n'Drop to Bidirectional to be able to copy stuff from your computer to VMs)
<br/><img src=""height="80%" width="80%" alt="5"/>
<br/><img src=""height="80%" width="80%" alt="6"/>
<br/><img src=""height="80%" width="80%" alt="3"/>
<br />
<br />

Start the VM. When it ask for DVD, locate to Window Server 2019 ISO file: <br/>
<a href="https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019">You can download the Window Server 2019 ISO right here <a>
<br/><img src="" height="80%" width="80%" alt="7"/> 
<br/><img src="" height="80%" width="80%" alt="8"/>
<br />
<br />

Decline all service and create a password. Ideally Password1 for home lab and something else complicate in real environment:  <br/>
<img src="" height="80%" width="80%" alt="14"/>
<br />
<br />

Log onto the VM. Rename your PC for better identifying (mine is DC). Go to network setting to setup IP  <br/>
Go to network setting on right down corner, click on the network setting, then choose "Change adapter options" <br/>
<img src="" height="80%" width="80%" alt="10"/>
<br />
<br />

Now, go status ➡️ detail and look at IPv4 Address to rename them (1 is internal and 1 is home internet) <br/>
 The 10.0.*.* will be your home internet <br>
 The 1**.**.*.* will be your internal netowrk <br>
<img src="" height="80%" width="80%" alt="11"/>
<br />
<br />

After rename them, go to Internal and change its properties: <br/>
<img src="" height="80%" width="80%" alt="12"/><br>

Go to Server Manager ➡️ Add roles and features ➡️ create an Active Directory, a DHCP Server and a DNS Serever<br/>
<img src="" height="80%" width="80%" alt="13"/><br>

Go Server Manager ➡️ Tools ➡️ Active Diractory Users and Computers. <br>
Create an organization unit, name it ADMIN and assign your own admin account in there. <br>
Go to account properties memberof add enter the object name domain admin <br/>
<img src="" height="80%" width="80%" alt="15"/><br>
<img src="" height="80%" width="80%" alt="17"/><br>
<img src="" height="80%" width="80%" alt="18"/><br>

Go Server Manager ➡️ Tools ➡️ Routing and Remote Access ➡️right click DC (local)➡️Configure and Enable Routing and Remote Access<br> <br/>
<img src="" height="80%" width="80%" alt="19"/><br>
 <br/>

 Next, go Server Manager ➡️ Tools ➡️ DHCP. Here we will set up a new scope for IPv4 for later on, manage devices that are in the network <br>
 Right click on IPv4 ➡️ New Scope ➡️ Name it (use the range of the scope, which is 100 - 200, so it will be 172.16.0.100-200. <br>
<img src="" height="80%" width="80%" alt="26"/><br>
 <img src="" height="80%" width="80%" alt="27"/><br>
 <img src="" height="80%" width="80%" alt="25"/><br>
 <br/> 
 
 Next, Start IP, end IP address,subnet mask, lengh setting like image below.<BR>
 Next, fill out Router option like below, click add to create router. AFter that, go next until finish <br>
 <img src="" height="80%" width="80%" alt="24"/><br>
 <img src="" height="80%" width="80%" alt="23"/><br>
 <img src="" height="80%" width="80%" alt="22"/><br>
 
 Right click on the domain to choose Authorize, then refresh IPv4
 <img src="" height="80%" width="80%" alt="21"/><br>

 Now come the fun part, PowerShell Script. Use this script
 <img src="" height="80%" width="80%" alt=""/><br>
 <img src="" height="80%" width="80%" alt=""/><br>
 <img src="" height="80%" width="80%" alt=""/><br>
 <img src="" height="80%" width="80%" alt=""/><br>
 <img src="" height="80%" width="80%" alt=""/><br>
 <img src="" height="80%" width="80%" alt=""/><br>
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
