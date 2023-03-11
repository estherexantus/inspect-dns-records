<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab we will be experimenting with DNS. This lab will help us have a better understanding of DNS.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory running in Azure on virtual machine
- A client machine running in Azure on virtual machine and joined to the domain

<h2>Lab Steps</h2>

<p>
<img src="https://i.imgur.com/xKePr4k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/yAlrhZw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
</p>
<p>
A-Record Exercise 
  <ul>
    <li>Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)</li>
    <li>Connect/log into Client-1 as an admin (mydomain\jane_admin)</li>
    <li>From Client-1 try to ping “mainframe” notice that it fails</li>
    <li>Nslookup “mainframe” notice that it fails (no DNS record)</li>
    <li>Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address</li>
    <li>Go back to Client-1 and try to ping it. Observe that it works.</li>
  </ul>
</p>
<br />

<p>
<img src="https://i.imgur.com/KYNmZMz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/80ARdZu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
</p>
<p>
In this exercise, we will load DNS cache and observe the change when updating mainframe's IP address.
   <ul>
    <li>Go back to DC-1 and change mainframe’s record address to 8.8.8.8</li>
    <li>Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address</li>
    <li>Observe the local dns cache (ipconfig /displaydns)</li>
    <li>Flush the DNS cache (ipconfig /flushdns). Observe that the cache is empty</li>
    <li>Attempt to ping “mainframe” again. Observe the address of the new record is showing up</li>
   </ul>
</p>
<br />

<p>
<img src="https://i.imgur.com/LgomfqN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/NovtDrd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
</p>
<p>
CNAME Record Exercise
  <ul>
    <li>Ping "search", you will observe that we are not able to find the host</li>
    <li>Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com”</li>
    <li>Go back to Client-1 and attempt to ping “search”</li>
    <li>You will observe that it is able to ping the site successfully.</li>
  </ul>
</p>


