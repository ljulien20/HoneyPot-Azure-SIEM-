         
<h1>HoneyPort Azure Cloud Project</h1>


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


<h2>Program walk-through:</h2>

<p align="center">
First,  I added a resource group to the subscription that has to be made to use Azure. Resource groups are a logical container used to organize and manage related cloud resources as a single unit. It allows administrators and developers to group services such as virtual machines, databases, storage accounts, and networking components that belong to the same application, project, or environment. By using resource groups, you can apply access controls, policies, and tags consistently across all included resources, making security, governance, and cost management easier.: <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450287844521148488/Screenshot_2025-12-15_184238.png?ex=694c894f&is=694b37cf&hm=f213dbfaf3cab56eacabd63ec878251062e643dac220e5f9365c6de8a48c2788" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
A virtual network was configured and validated inside the resource group:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450290075014397964/Screenshot_2025-12-15_185332.png?ex=694c8b62&is=694b39e2&hm=ee4658cc90af608851bc7ea674a3fa3d3d43141871612f694e00faba8868c28a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />  
<br />
A Virtual machine is then created and deployed as "AIE-NET-WEST-1": <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450291367979782214/Screenshot_2025-12-15_183156.png?ex=694c8c97&is=694b3b17&hm=440b5b40cddcdb69fe91080a2e6edfc108e752b57b570e1f0eda4a9a3b2a0713&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450291368487551209/Screenshot_2025-12-15_183233.png?ex=694c8c97&is=694b3b17&hm=a1da7247cf0f1c4651a7a447beb811ae837fde335fad4ec6027fa28d35a33769&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once the virtual machine was created, I configured the virtual network firewall to be turned off under a new inbound security rule. Destination port ranges will be changed to *, which indicates any range. Priority can be what number is available. I have already made this rule using 100, so here I used 110.:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450300523789025351/Screenshot_2025-12-15_190057.png?ex=694c951e&is=694b439e&hm=df06066a62fdb064a7500526a76e1aa1c7d286fd1ca44bd52e741dd275cab364&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450300524351066220/Screenshot_2025-12-15_190316.png?ex=694c951e&is=694b439e&hm=b8774c4fa171fd89c9bc57b179c1cc54a46af16a7ddfeab5853a8cb3eae5814f&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450300524858441800/Screenshot_2025-12-15_190601.png?ex=694c951e&is=694b439e&hm=3243e796d9d50cbe31c1b10097f315625b9fd68b83e57871e3a991196c40ba83&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After the new inbound rule is configured in the virtual network, use Remote Desktop Connection to access the virtual machine via IP address. When you in the desktop, go to Windows Defender Firewall properties, turn all tabs off in that window 
:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450303046532993084/Screenshot_2025-12-15_194131.png?ex=694c9777&is=694b45f7&hm=6ed0c9f216922232b1d1fee5d3e3d6dbf8c6c2570f5b39fd6b762611675657fe" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now test the connection to make sure access is open to you and the public web. Open the command prompt and ping the virtual machine IP address. My subscription is past the 30-day trial period, which means my network is not turned on for my virtual machine, but if this is your first account, then your network should be accessible. You should have more than 0 received packets and less than 50% loss if your virtual network is on.:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450305633751400601/Screenshot_2025-12-15_195133.png?ex=694c99e0&is=694b4860&hm=aa39256e098a1faa9b3e089fd9e64da78b1439a87fa328649558ea4d28075304" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log analytics workspace is created  to collect data entries of potential attacks and will be linked to Microsoft Sentinel (SIEM tool) as a directory:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450309681598955633/Screenshot_2025-12-15_200844.png?ex=694bf4e5&is=694aa365&hm=5e17c01345423f4884722870aaa399605b775564dd7baa995cbda0db9ea60a5b&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450309682215387166/Screenshot_2025-12-15_201138.png?ex=694bf4e5&is=694aa365&hm=c27401f481b92c31115f87bf8520aef5206b0e46d26d84025739a31fa29a261d&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once in Microsoft Sentinel, create a log space using data from your resource group that has your virtual machine:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450314148037791855/Screenshot_2025-12-15_202802.png?ex=694bf90e&is=694aa78e&hm=2cc0ea34f984d05048f72992d667fd65e3a3379d64676f27e5edae64a6c21327" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
You can find KQL under the logs tab, where you can search all data within your virtual machine:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450315443272286268/Screenshot_2025-12-15_203454.png?ex=694bfa43&is=694aa8c3&hm=52cdfa62ec4ff9db82500c23de5c49ec4b1deec9d8c6f993243fcf535a4ca0b4" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
You will create a workbook with your KQL queries and input them to make a map of all attacks in the world:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450316287938134116/Screenshot_2025-12-15_203735.png?ex=694bfb0c&is=694aa98c&hm=d0fca01220dc3911d181f4d6858efc4526e4270b3bafc0355096e05ec90690b0" height="80%" width="80%" alt="Disk Sanitization Steps"/>
I added a map.json code that inputs all queries into a map to be easier to read and can be used for reports. This is the completed VM attack map worldwide within 24 hours of being open:  <br/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450321333782319135/Screenshot_2025-12-15_204207.png?ex=694bffbf&is=694aae3f&hm=ff47d10726f255528d1ffdad4dc2964bbde1980ebc28ed2cd32f9853748821f6&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450321334373453855/Screenshot_2025-05-13_082456.png?ex=694bffbf&is=694aae3f&hm=cd08fe318f40583c9dd97c1871954fc5560c36805f7474dcde0dfe4e21d12ddd&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1445251151896248323/1450321334927233215/Screenshot_2025-05-13_083904.png?ex=694bffbf&is=694aae3f&hm=175a42d5f5a19dc763ed75d33b517eda86085bafbdaa7d56a25bafe433a5c964&" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
