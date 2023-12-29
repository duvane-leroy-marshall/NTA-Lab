# NTA-Lab
A HackTheBox Academy module focusing on analyzing network traffic for anomalies.

<h1>Intro to Network Traffic Analysis</h1>

[Module Link](https://academy.hackthebox.com/course/preview/intro-to-network-traffic-analysis)

<h2>Description</h2>
This lab introduces the concept of network traffic analysis by covering the principles of NTA and using traffic analysis tools such as Wireshark and tcpdump.

This lab covers the following:

- <b>Network traffic analysis principles</b>
- <b>Tcpdump fundamentals</b>
- <b>Working with Wireshark</b>
- <b>Wireshark filters</b>

<h2>Tools Used</h2>

- <b>Wireshark</b> 
- <b>Tcpdump</b>

<h2>Environments Used </h2>

- <b>HackTheBox Pwnbox Linux</b>
- <b>Windows 11</b>

<h2>Using Tcpdump:</h2>

<p align="center">
Tcpdump Switch Commands: <br/>
<img src="https://i.imgur.com/usCi2bU.jpg" height="80%" width="80%" alt="Tcpdump Switch Commands"/>
<br />
<br />
Locate Tcpdump: <br/>
<img src="https://i.imgur.com/sZn11Kw.jpg" height="80%" width="80%" alt="Locate Tcpdump"/>
<br />
<br />
Install Tcpdump:  <br/>
<img src="https://i.imgur.com/HMHnWKA.jpg" height="80%" width="80%" alt="Install Tcpdump"/>
<br />
<br />
Tcpdump Version Validation: <br/>
<img src="https://i.imgur.com/3yJo4o5.jpg" height="80%" width="80%" alt="Tcpdump Version"/>
<br />
<br />
Listing Avaliable Interfaces:  <br/>
<img src="https://i.imgur.com/Sm2zq4S.jpg" height="80%" width="80%" alt="Listing Interfaces"/>
<br />
<br />
Traffic Captures with Tcpdump:  <br/>
<img src="https://i.imgur.com/UIBmhWv.jpg" height="80%" width="80%" alt="Traffic Capture"/>
<br />
<br />
Saving PCAP Output to a File:  <br/>
<img src="https://i.imgur.com/HZ3AFYH.jpg" height="80%" width="80%" alt="Saving PCAP Output"/>
<br />
<br />
Reading Output From a File:  <br/>
<img src="https://i.imgur.com/DNe7zy6.jpg" height="80%" width="80%" alt="Reading PCAP Output"/>
<br />
<br />
Tcpdump Filters:  <br/>
<img src="https://i.imgur.com/K3dYKIS.jpg" height="80%" width="80%" alt="Tcpdump Filters"/>
<br />
<br />
Hunting for a SYN Flag:  <br/>
<img src="https://i.imgur.com/XnX8hFv.jpg" height="80%" width="80%" alt="SYN Flag"/>
<br />
<br />

<h2>Using Wireshark:</h2>

<p align="center">
Wireshark Capture on eth0 Interface: <br/>
<img src="https://i.imgur.com/InB6Edm.jpg" height="80%" width="80%" alt="Wireshark Capture"/>
<br />
<br />
Wireshark Capture Filter: <br/>
<img src="https://i.imgur.com/bqeGk8k.jpg" height="80%" width="80%" alt="Wireshark Capture Filter"/>
<br />
<br />
Wireshark Display Filter: <br/>
<img src="https://i.imgur.com/D3ct0lE.jpg" height="80%" width="80%" alt="Wireshark Display Filter"/>
<br />
<br />

<h2>Guided Lab: Traffic Analysis Workflow using Wireshark</h2>
In this guided lab scenario, one of our fellow admins noticed a weird connection from Bob's host IP when analyzing baseline captures. He asked us to check it out and see what is happening. 
<br />
<br />
We will investigate a saved capture in Wireshark to find any anomalies.
<br />
<br />

<p align="center">
Using the Conversation plugin to see the different hosts using IPv4: <br/>
<img src="https://i.imgur.com/6mNztCV.jpg" height="80%" width="80%" alt="Conversation Plugin"/>
<br />
<b>As we can see from the conversation plugin, there are three conversations captured.</b>
<br />
<br />
Using the Protocol Hierarchy plugin to look into the amount of traffic: <br/>
<img src="https://i.imgur.com/8PIT9Q3.jpg" height="80%" width="80%" alt="Protocol Hierarchy Plugin"/>
<br />
<b>According to the protocol hierarchy plugin, it is mostly TCP traffic in this capture. Since there is less UDP than TCP, we will be looking into UDP first.</b>
<br />
<br />
Filtering out TCP to investigate anything unsual: <br/>
<img src="https://i.imgur.com/QiYG3Zj.jpg" height="80%" width="80%" alt="TCP Filter"/>
<br />
<b>Judging by our filter, there is nothing out of the ordinary. Next is setting a filter to display TCP traffic.</b>
<br />
<br />
Filtering out UDP and ARP: <br/>
<img src="https://i.imgur.com/4BdbdYL.jpg" height="80%" width="80%" alt="UDP ARP Filter"/>
<br />
<b>We can see at packet 3 that the session was established via a three-way handshake.</b>
<br />
<br />
Looking at a TCP Stream to dig deeper: <br/>
<img src="https://i.imgur.com/esACySn.jpg" height="80%" width="80%" alt="TCP Stream-1"/>
<br />
<img src="https://i.imgur.com/lzu3lv7.jpg" height="80%" width="80%" alt="TCP Stream-2"/>
<br />
<b>When we followed the TCP stream, we found something suspicious. It appears someone is issuing commands like whoami, ipconfig, dir. More alarming is that someone made an account called hacker and assigned itself to the administrators group on the host.</b>
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
