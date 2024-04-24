<h1>Elk in the Cloud</h1>

<h2>Description</h2>
In this lab, I will be setting up an Elastic Instance using a free trial.<br />
<br />
ELK stands for Elasticsearch, Logstash, and Kibana; ELK stack combines these three technologies and provides a solution when working with large sets of data. Elk enables defenders by allowing them to detect attacks and conduct threat hunting within the same platform. We can set up SIEM rules to alert us to attacks, work with dashboards, scale to your own needs, and more.
<br />

<h2>Applications and Utilities Used</h2>

- <b>Elastic cloud</b> 
- <b>Kibana</b>
- <b>Sysmon</b>

<h2>Environments Used </h2>

- <b>Windows Virtual Machine</b>

<h2>Lab Walk-through</h2>

<p align="center">
1. The first thing we are going to do after setting up our free trial account and the instance is integrating Kibana. This can be done by going to the top search bar looking for Kibana and selecting “integrate.”: <br/>
<img src="https://imgur.com/WtRRqR1.png" height="80%" width="80%" alt="ELK in the Cloud"/>
<br />
<br />
2. This will bring us to a screen that allows you to install the Elastic Agent on your host. In my setup, I am running a Windows VM, so I will select the Windows tab and copy that text to a .txt file.:  <br/>
<img src="https://imgur.com/Ef98uIl.png" height="80%" width="80%" alt="ELK in the Cloud"/>
<br />
<br />
3. Next to install we will run PowerShell as administrator and copy over the information we put in the .txt file. Make sure to hit Y to run the service when prompted.: <br/>
<img src="https://imgur.com/O6Rf8Qd.png" height="80%" width="80%" alt="ELK in the Cloud"/>
<br />
<br />
4. When you go back to the Kibana set up you can confirm that you have enrolled with the agent successfully and add the integration. On the next page, we will leave the default settings and confirm the incoming data.:  <br/>
<img src="https://imgur.com/zwYcsWl.png" height="80%" width="80%" alt="ELK in the Cloud"/>
 <br />
<br />
5. To make sure our device has successfully connected, we can navigate management, and check out our fleet. If done correctly, you will see the desktop that you added.:  <br/>
<img src="https://imgur.com/k89xjJK.png" height="80%" width="80%" alt="ELK in the Cloud"/><br />
<br />
6. 6.)	To help make our logs more readable we will download Sysmon. Once Sysmon is downloaded you can navigate back to PowerShell and start Sysmon as a service.:  <br/>
<img src="https://imgur.com/PN5gnBA.png" height="80%" width="80%" alt="ELK in the Cloud"/><br />
<br />
7. Now that Sysmon is running, we need to set up our Elastic agent to be able to gather these logs. Navigate to management and click on integrations.:  <br/>
<img src="https://imgur.com/r2geYQP.png" height="80%" width="80%" alt="ELK in the Cloud"/><br />
<br />
8. Search for Windows and click on the second option, then click on the add Windows to add the Windows integration.:  <br/>
<img src="https://imgur.com/uU1s5xm.png" height="80%" width="80%" alt="ELK in the Cloud"/>
 <br />
<br />
9. By default the Sysmon log channel should be activated. We can confirm it is activated by looking under the “Collect events from the following Windows event log channels:” section. :  <br/>
<img src="https://imgur.com/2VE7Pzs.png" height="80%" width="80%" alt="ELK in the Cloud"/>
 <br />
<br />
10. After confirming go ahead and save. Make sure when you do save it to your existing agent policy. Now when you navigate back to your installed integrations, you can confirm that you have a Windows integration policy set up under your agent policy.:  <br/>
<img src="https://imgur.com/xHFLEWF.png" height="80%" width="80%" alt="ELK in the Cloud"/>
 <br />
<br />
11. At this point your instance should be receiving logs. To test this, we can play around with the computer that this is installed on by creating new directories, starting applications, etc.  <br/>
 <br />
<br />
12. After you have created some log activity we can navigate to discover by clicking the hamburger menu. To view just the Sysmon logs we can add a filter.:  <br/>
<img src="https://imgur.com/iVn4hgs.png" height="80%" width="80%" alt="ELK in the Cloud"/>
 <br />
<br />
13. This should result in some logs that you generated. Now we can add some of the available fields and see some of the events that went on. I added event.action, event.code and agent.name just to visualize the actions we did in our environment.:  <br/>
<img src="https://imgur.com/Pcbwo10.png" height="80%" width="80%" alt="ELK in the Cloud"/>
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
