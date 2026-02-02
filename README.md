<h1>Azure Honeypot</h1>

<h2>Description</h2>
Project consists of a walkthrough for a honeypot deployed on Azure with Sentinel and Log Analytics.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Sentinel</b> 
- <b>KQL</b> 
- <b>Azure</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (22H2)

<h2>Walk-through:</h2>

<p align="center">
1.	Create the Resource Group <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />
  
2.	Create the Virtual Network  <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />
  
3.	Create the Virtual Machine <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />
  
4.	Expose VM to the Internet  <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />
  
5.	Remote into VM and Disable Firewall  <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />

6.	Creating the Log Analytics Workspace <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />
  
7.	Linking Microsoft Sentinel <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />

8.	Connect VM to Log Analytics Workspace <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />

9.	Querying with KQL <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />

10.	Creating the Watchlist <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />

11.	Creating the Threat Map <br/>
<img src="" height="80%" width="80%" alt=""/>
<br />
<br />

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
