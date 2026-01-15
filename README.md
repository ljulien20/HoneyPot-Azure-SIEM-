         
<h1>HoneyPot Azure Cloud Project</h1>


<h2>Description</h2>
A SIEM Cloud project was created today using Azure cloud infrastructure. In this project, I created a virtual machine, a network security group, an SQL database, and a virtual network to detect real-time attackers targeting the virtual website that will be built within the virtual network, also known as a honeypot. The data collected will be forwarded to logs in a centralized repository.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Command Promt</b> 
- <b>KQL/SQL</b>
- <b>Remote Desktop Connection</b>

<h2>Environments Used </h2>

- <b>Windows 11</b> 
- <b>AZURE</b>
- <b>Micorsoft Sentinel</b>
- <b>Virtual Machines</b>


<h2>Program walk-through:</h2>

<p align="center">
First,  I added a resource group to the subscription that has to be made to use Azure. Resource groups are a logical container used to organize and manage related cloud resources as a single unit. It allows administrators and developers to group services such as virtual machines, databases, storage accounts, and networking components that belong to the same application, project, or environment. By using resource groups, you can apply access controls, policies, and tags consistently across all included resources, making security, governance, and cost management easier.: <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450287844521148488/Screenshot_2025-12-15_184238.png?ex=69698a4f&is=696838cf&hm=95ff66b46faae302b44eea9be645204f8c84a05d3e718d793384ece5f3d9ed0d" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
A virtual network was configured and validated inside the resource group:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450290075014397964/Screenshot_2025-12-15_185332.png?ex=69698c62&is=69683ae2&hm=951166479b4ee0f9c43635965d38910416f1d34c8ed6d8fe403c5f188fbc7a12" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />  
<br />
A Virtual machine is then created and deployed as "AIE-NET-WEST-1": <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450291367979782214/Screenshot_2025-12-15_183156.png?ex=69698d97&is=69683c17&hm=b61501ed00e3f65dfd31cf7995a413fd34427f42b879cb8a636933986c83d1ac&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450291368487551209/Screenshot_2025-12-15_183233.png?ex=69698d97&is=69683c17&hm=a21870b8b36982528845f529a52d428e92d77d15ef4f7c480360c4c40557ed9e&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once the virtual machine was created, I configured the virtual network firewall to be turned off under a new inbound security rule. Destination port ranges will be changed to *, which indicates any range. Priority can be what number is available. I have already made this rule using 100, so here I used 110:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450300523789025351/Screenshot_2025-12-15_190057.png?ex=6969961e&is=6968449e&hm=8840a2379a21e2c94ea63cc1f33a0327f8b1253b70aff8d4543e6a814cc97d9a&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450300524351066220/Screenshot_2025-12-15_190316.png?ex=6969961e&is=6968449e&hm=b6be7ebb44be158839b7f931669caf56bd43fdcf2cb4e2f3d9a942df093433b5&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450300524858441800/Screenshot_2025-12-15_190601.png?ex=6969961e&is=6968449e&hm=808ae8c1ef12e3e70a7c4a51670ba85192237f37791872916c9526d7f47ec884&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After the new inbound rule is configured in the virtual network, use Remote Desktop Connection to access the virtual machine via IP address. When you in the desktop, go to Windows Defender Firewall properties, turn all tabs off in that window:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450303046532993084/Screenshot_2025-12-15_194131.png?ex=69699877&is=696846f7&hm=51b4a16a46d8e421c0f179b01d78764f075c9099a483102c3cc8d9d4a94eeb51" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
         
Now test the connection to make sure access is open to you and the public web. Open the command prompt and ping the virtual machine IP address. My subscription is past the 30-day trial period, which means my network is not turned on for my virtual machine, but if this is your first account, then your network should be accessible. You should have more than 0 received packets and less than 50% loss if your virtual network is on.:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450305633751400601/Screenshot_2025-12-15_195133.png?ex=69699ae0&is=69684960&hm=3b3c5895d1d9346a77fd85d0027226392432e21a3994aed0881c7f64d05b7094" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log analytics workspace is created  to collect data entries of potential attacks and will be linked to Microsoft Sentinel (SIEM tool) as a directory:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450309681598955633/Screenshot_2025-12-15_200844.png?ex=69699ea5&is=69684d25&hm=e4fbfb86b9cb7644b13900ec6e125d064c85a691964f98927dcf67388372f304&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450309682215387166/Screenshot_2025-12-15_201138.png?ex=69699ea5&is=69684d25&hm=04d1e3bf6e976bbd4bfc2b2322a28d8a428d35fa85672aca6a6faac81c31147e&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once in Microsoft Sentinel, create a log space using data from your resource group that has your virtual machine:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450314148037791855/Screenshot_2025-12-15_202802.png?ex=6969a2ce&is=6968514e&hm=57cd8167cb79939b4da12e9b841406d6074591e5b31e7b67f35d50b19f5d286b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
You can find KQL under the logs tab, where you can search all data within your virtual machine:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450315443272286268/Screenshot_2025-12-15_203454.png?ex=6969a403&is=69685283&hm=c60dec2194eb807ee3c5a8de6cc326691bd1deb441c633002eb5af2d046a0593" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
You will create a workbook with your KQL queries and input them to make a map of all attacks in the world:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450316287938134116/Screenshot_2025-12-15_203735.png?ex=6969a4cc&is=6968534c&hm=389482ea720bc63130e22d30d45fd4484fa04533246d7f7af078f91090c3bbaa" height="80%" width="80%" alt="Disk Sanitization Steps"/>

I added a map.json code that inputs all queries into a map to be easier to read and can be used for reports. This is the completed VM attack map worldwide within 24 hours of being open:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450321333782319135/Screenshot_2025-12-15_204207.png?ex=6969a97f&is=696857ff&hm=6ca6ca82bd1099abd1084c943b93ba3413b43face58987133a3101266b39fe9e&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450321334373453855/Screenshot_2025-05-13_082456.png?ex=6969a97f&is=696857ff&hm=31de6b9d83a6962c2bca8978b9d5115e446b2168ba039b0a92f3a190965e8a60&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450321334927233215/Screenshot_2025-05-13_083904.png?ex=6969a97f&is=696857ff&hm=78d7fb7777286c746a719d5ca73e39839903bec3ed1abd0f2b11e8e9faccd6f0&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
