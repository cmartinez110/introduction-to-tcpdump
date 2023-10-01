<h1>Introduction to TCPDump</h1>


<h2>Description</h2>
Use TCPDump to capture and analyze packets. As I become more proficient, I will update my portfolio with better projects (maybe Hexadecimal and ASCII analysis?).
<br />


<h2>Languages and Utilities Used</h2>

- <b>Bash</b> 
- <b>TCPDump</b>

<h2>Environments Used </h2>

- <b>Linux</b>

<h2>Program walk-through:</h2>

<p align="center">
"sudo ifconfig" identifies network interfaces that are available. "sudo tcpdump -D" also helps to identify which interfaces are available: <br/>
<img src="https://i.imgur.com/wwlOfIc.png" height="80%" width="80%" alt="tcpdump"/>
<br />
<br />
"sudo tcpdump -i eth0 -v -c5" selects eth0 as the interface to listen on."-v" selects the verbose option. "c5" selects 5 packets to be captured. On the first line of the returned packet data, we can see thst eth0 is the selected interface. We can also see the size in bytes. On line 2 we see the timestamp and protocl type (IP). The information provided by the verbose option, such as TTL, flags, etc. ">" indicates direction of the traffic:  <br/>
<img src="https://i.imgur.com/TBNs80y.png" height="80%" width="80%" alt="tcpdump"/>
<br />
<br />
"sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &" 
    "-i eth0" will capture data from the eth0 interface. "-nn" will not attempt to resolve IP addresses or ports to names. Two benefits of thisare that the lookup data may not be valid. It also prevents malicious actors from being alerted to an investigation. "-c9" captures 9 packets of data and then exit. "port 80" filter only port 80 traffic. This is the default HTTP port. "-w" capture.pcap: Save the captured data to the named file.
    "&" is an instruction to the Bash shell to run the command in the background: <br/>
<img src="https://i.imgur.com/Ge233tV.png" height="80%" width="80%" alt="tcpdump"/>
<br />
<br />
"curl opensource.google.com" generates some traffic to be captured. "ls -l capture.pcap" helps to verify. "sudo tcpdump -nn -r capture.pcap -v" prevents name lookup, reads capture data from named file, and provides verbose details. "sudo tcpdump -nn -r capture.pcap -X" does the same, but "-X" displays the hexadecimal and ASCII output format packet data. Hexadecimal and ASCII output can be analyzed to detect patterns or anomalies during malware analysis or forensic analysis:  <br/>
<img src="https://i.imgur.com/j106dxD.png" height="80%" width="80%" alt="tcpdump"/>
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
