         
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
First,  I added a resource group to the subscription that has to be made to use Azure. Resource groups are a logical container used to organize and manage related cloud resources as a single unit. It allows administrators and developers to group services such as virtual machines, databases, storage accounts, and networking components that belong to the same application, project, or environment. By using resource groups, you can apply access controls, policies, and tags consistently across all included resources, making security, governance, and cost management easier: <br/>
<img width="1273" height="1144" alt="Screenshot 2025-12-15 181738" src="https://github.com/user-attachments/assets/8cb82125-c5be-46f2-8796-3b78b34e124a" />
<br />
<br />
A virtual network was configured and validated inside the resource group:  <br/>
<img width="1250" height="893" alt="Screenshot 2025-12-15 184238" src="https://github.com/user-attachments/assets/7d8df778-c40d-45a9-9bed-e5d4618eb09e" />
<br />  
<br />
A Virtual machine is then created and deployed as "AIE-NET-WEST-1": <br/>
<img width="960" height="997" alt="Screenshot 2025-12-15 183233" src="https://github.com/user-attachments/assets/5b07919c-fa47-4782-b814-26d811ae011b" />
<br />
<br />
Once the virtual machine was created, I configured the virtual network firewall to be turned off under a new inbound security rule. Destination port ranges will be changed to *, which indicates any range. Priority can be what number is available. I have already made this rule using 100, so here I used 110:  <br/>
<img width="1268" height="1012" alt="Screenshot 2025-12-15 190057" src="https://github.com/user-attachments/assets/97d419c1-6013-474d-ba1a-e74df51d9c85" />
<img width="1271" height="815" alt="Screenshot 2025-12-15 190316" src="https://github.com/user-attachments/assets/c4cab39c-780d-4332-86ea-b851368668a3" />
<img width="1243" height="1157" alt="Screenshot 2025-12-15 190601" src="https://github.com/user-attachments/assets/f5320232-707c-4cb8-9ea1-a8a6748e756e" />
<br />
<br />
After the new inbound rule is configured in the virtual network, use Remote Desktop Connection to access the virtual machine via IP address. When you in the desktop, go to Windows Defender Firewall properties, turn all tabs off in that window:  <br/>
<img width="1224" height="891" alt="Screenshot 2025-12-15 194131" src="https://github.com/user-attachments/assets/8cc5b3c8-2593-41f8-9312-d2aa1cbc9213" />
<br />
         
Now test the connection to make sure access is open to you and the public web. Open the command prompt and ping the virtual machine IP address. My subscription is past the 30-day trial period, which means my network is not turned on for my virtual machine, but if this is your first account, then your network should be accessible. You should have more than 0 received packets and less than 50% loss if your virtual network is on.:  <br/>
<img width="1098" height="634" alt="Screenshot 2025-12-15 195133" src="https://github.com/user-attachments/assets/4cd1b2fe-6782-4bc7-b015-5fd749ddbd59" />
<br />
<br />
Log analytics workspace is created  to collect data entries of potential attacks and will be linked to Microsoft Sentinel (SIEM tool) as a directory:  <br/>
<img width="1247" height="947" alt="Screenshot 2025-12-15 200844" src="https://github.com/user-attachments/assets/e079b481-8015-4d52-8f7a-712ded781f14" />
<img width="1257" height="308" alt="Screenshot 2025-12-15 201138" src="https://github.com/user-attachments/assets/7e21c9c5-9112-4094-a932-c037cb095cba" />
<br />
<br />
Once in Microsoft Sentinel, create a log space using data from your resource group that has your virtual machine:  <br/>
<img width="1202" height="661" alt="Screenshot 2025-12-15 202802" src="https://github.com/user-attachments/assets/aab92835-2889-4cac-891d-f12b442091ee" />
<br />
You can find KQL under the logs tab, where you can search all data within your virtual machine:  <br/>
<img width="1262" height="1142" alt="Screenshot 2025-12-15 203454" src="https://github.com/user-attachments/assets/b440a827-d1b0-4bf6-9be5-34fb56fb2cc3" />
<br />
You will create a workbook with your KQL queries and input them to make a map of all attacks in the world:  <br/>
<img width="1044" height="616" alt="Screenshot 2025-12-15 203735" src="https://github.com/user-attachments/assets/c3942dee-972b-4333-a7ef-2a6ec785f669" />
I added a map.json code that inputs all queries into a map to be easier to read and can be used for reports. This is the completed VM attack map worldwide within 24 hours of being open:  <br/>
<img width="1251" height="1012" alt="Screenshot 2025-12-15 204207" src="https://github.com/user-attachments/assets/6c7052bf-b586-4d6d-817e-2615fe9417ee" />
<img width="2213" height="1157" alt="Screenshot 2025-05-12 184031" src="https://github.com/user-attachments/assets/614de90a-eaa5-4a8d-809b-f974544b318a" />
<img width="1384" height="816" alt="Screenshot 2025-05-13 083904" src="https://github.com/user-attachments/assets/b86d4817-8bec-4cea-849b-f082853f9a15" />

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
