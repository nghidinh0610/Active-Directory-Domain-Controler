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

Launch the utility: <br/>
<img src="https://i.imgur.com/jOSr9Yd.png" height="80%" width="80%" alt="9"/><br />
 
This is the setting of the 2 VM we will create. DC will be the domain controler and CLIENT1 is just a VM to test log in information 
<br />
<img src="https://i.imgur.com/jkt1f1J.png" height="80%" width="80%" alt="1"/><br>
<img src="https://i.imgur.com/emjNlqC.png" height="80%" width="80%" alt="2"/><br>
<br />

Setting up 2 network in DC, 1 NAT (to connect to your home internet) and 1 internal (for VM):  <br>
(Additionally, change Shared Clipboard and Drag'n'Drop to Bidirectional to be able to copy stuff from your computer to VMs)
<br/><img src="https://i.imgur.com/dLFvsJz.png" height="80%" width="80%" alt="5"/>
<br/><img src="https://i.imgur.com/MqkSzDF.png" height="80%" width="80%" alt="6"/>
<br/><img src="https://i.imgur.com/SU1PhXm.png" height="80%" width="80%" alt="3"/>
<br />
<br />

Start the VM. When it ask for DVD, locate to Window Server 2019 ISO file: <br/>
<a href="https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019">You can download the Window Server 2019 ISO right here <a>
<br/><img src="https://i.imgur.com/nt0WEGL.png" height="80%" width="80%" alt="7"/> 
<br/><img src="https://i.imgur.com/kA4dr7w.png" height="80%" width="80%" alt="8"/>
<br />
<br />

Decline all service and create a password. Ideally Password1 for home lab and something else complicate in real environment:  <br/>
<img src="https://i.imgur.com/VbfQM1E.png" height="80%" width="80%" alt="14"/>
<br />
<br />

Log onto the VM. Rename your PC for better identifying (mine is DC). Go to network setting to setup IP  <br/>
Go to network setting on right down corner, click on the network setting, then choose "Change adapter options" <br/>
<img src="https://i.imgur.com/fBVXDAx.png" height="80%" width="80%" alt="10"/>
<br />
<br />

Now, go status ➡️ detail and look at IPv4 Address to rename them (1 is internal and 1 is home internet) <br/>
 The 10.0.*.* will be your home internet <br>
 The 1**.**.*.* will be your internal netowrk <br>
<img src="https://i.imgur.com/z4GMJzf.png" height="80%" width="80%" alt="11"/>
<br />
<br />

After rename them, go to Internal and change its properties: <br/>
<img src="https://i.imgur.com/QEJuIzO.png" height="80%" width="80%" alt="12"/><br>

Go to Server Manager ➡️ Add roles and features ➡️ create an Active Directory, a DHCP Server and a DNS Serever<br/>
<img src="https://i.imgur.com/6QuV8kl.png" height="80%" width="80%" alt="13"/><br>

In Server Manager, complete DHCP config<br>
<img src="https://i.imgur.com/nLR37qJ.png" height="80%" width="80%" alt="20"/><br>

Go Server Manager ➡️ Tools ➡️ Active Diractory Users and Computers. <br>
Create an organization unit, name it ADMIN and assign your own admin account in there. <br>
Go to account properties memberof add enter the object name domain admin <br/>
<img src="https://i.imgur.com/X40r7C6.png" height="80%" width="80%" alt="15"/><br>
<img src="https://i.imgur.com/02kyUBF.png" height="80%" width="80%" alt="17"/><br>
<img src="https://i.imgur.com/x1pn1AF.png" height="80%" width="80%" alt="18"/><br>

Go Server Manager ➡️ Tools ➡️ Routing and Remote Access ➡️right click DC (local)➡️Configure and Enable Routing and Remote Access<br> <br/>
<img src="https://i.imgur.com/m7hYhLL.png" height="80%" width="80%" alt="19"/><br>
 <br/>

 Next, go Server Manager ➡️ Tools ➡️ DHCP. Here we will set up a new scope for IPv4 for later on, manage devices that are in the network <br>
 Right click on IPv4 ➡️ New Scope ➡️ Name it (use the range of the scope, which is 100 - 200, so it will be 172.16.0.100-200. <br>
<img src="https://i.imgur.com/sqevAxl.png" height="80%" width="80%" alt="26"/><br>
 <img src="https://i.imgur.com/g9lyLMf.png" height="80%" width="80%" alt="27"/><br>
 <img src="https://i.imgur.com/oSyVEcg.png" height="80%" width="80%" alt="25"/><br>
 <br/> 
 
 Next, Start IP, end IP address,subnet mask, lengh setting like image below.<BR>
 Next, fill out Router option like below, click add to create router. AFter that, go next until finish <br>
 <img src="https://i.imgur.com/ncCNxxL.png" height="80%" width="80%" alt="24"/><br>
 <img src="https://i.imgur.com/Oyif5Kx.png" height="80%" width="80%" alt="23"/><br>
 <img src="https://i.imgur.com/OFwARaU.png" height="80%" width="80%" alt="22"/><br>
 
 Right click on the domain to choose Authorize, then refresh IPv4<br>
 <img src="https://i.imgur.com/YGCniu6.png" height="80%" width="80%" alt="21"/><br>

 Now come the fun part, PowerShell Script. Use <a href="https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbmZMZVlzRU5seVA2QUpxa1dVZXNfckJyejRsUXxBQ3Jtc0tsWTZVRk8wR0x3ODIxVHpWUUItaDdOTzB3VVA2ajlpbnEyN1BkMW5nSFJ2Sm5pQ0pOVEdqTURkN1FPVFdqdnQ0XzlPcXFUU2FTT0xBb2d4RDVzSm85YkVlNUpWSGs3ZExzUzI4eHpNWWp5TGNmc3lDbw&q=https%3A%2F%2Fgithub.com%2Fjoshmadakor1%2FAD_PS%2Farchive%2Frefs%2Fheads%2Fmaster.zip&v=MHsI8hJmggI">this link <a> to download the script script <br>
 Extract the file. Open name.txt and add your own name (2 words) <br>
 <img src="https://i.imgur.com/bqvrWyW.png" height="80%" width="80%" alt="28"/><br>
 
 Run the PowerShell ISE as administrator, then run the script (F5). Some error will show but it will not matter
 <img src="https://i.imgur.com/gsV2KC8.png" height="80%" width="80%" alt="29"/><br>
 <img src="https://i.imgur.com/6s6EMsC.png" height="80%" width="80%" alt="30"/><br>
 
 So, that's it for the Domain Controler. Now our next step would be create an example of a computer that is under this domain <br>
 Go to Oracle VM VirtualBox, create a new VM, name it CLIENT1<br>
 <img src="https://i.imgur.com/pt2d3fp.png" height="80%" width="80%" alt="33"/><br>
 
 Go to setting, Shared Clipboard and Dra'n'Drop should both be Bidirectional<br>
 Network, change it from NAT to Internal Network<br> 
 <img src="https://i.imgur.com/DCgV3by.png" height="80%" width="80%" alt="31"/><br>
 <img src="https://i.imgur.com/hJFZrQ1.png" height="80%" width="80%" alt="32"/><br>
 
 Start the VM. This time, choose window 10 instead. <br>
 You can get windown 10 by download <a href="">this <a>, run it and wait until it finish creating ISO file. Choose the ISO file <br>
 <img src="https://i.imgur.com/L0xLbD8.png" height="80%" width="80%" alt="34"/><br>
 
 Go forward, decline all service and create a local account instead (it will try to make you create an online account) <br>
 After you're done with setting up the window, right click on window icon ➡️ System ➡️ Scroll down the Rename this PC (advance)<br>
 <img src="https://i.imgur.com/ercnHRq.png" height="80%" width="80%" alt="35"/><br>
 
 Then go to Change, change your computer name to something make sense (CLIENT1 is good), then choose member of Domain, type in your domain<br>
 <img src="https://i.imgur.com/1iIGD9Y.png" height="80%" width="80%" alt="36"/><br>
 
 Now, this one happened to me. When I do this, it say can't find the domain<br>
 Don't panic. You are still on the right track. Go to Oracle VM VirtualBox, go to setting ➡️ network, check if it's internal. Mine they always change back to NAT, even I have changed earlier. Now you should see your own domain.<br>
 This dialog will show up if things go through. Use admin account you created earlier to log on, the restart it.<br>
 <img src="https://i.imgur.com/oFrefZS.png" height="80%" width="80%" alt="37"/><br>
 
There you go, you got your first Active Directory created

<h2>Conclusion</h2>
Active Directory is essential for every organization to manage their network traffic and make sure there is no unauthorize user got into the internal network or some leech to external party. It's also a basic principal for all IT professional to know and learn no matter what your main role is. Hope you find this blog informative and helpful<br>

### [LINK TO THE ORIGINAL YOUTUBE TUTORIAL](https://www.youtube.com/watch?v=MHsI8hJmggI&t=2135s)
