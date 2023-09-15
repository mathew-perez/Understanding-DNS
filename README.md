<p align="center">
<img src="https://i.imgur.com/rUZwyvW.jpg" height="80%" width="80%" alt="How DNS Works"/>
</p>

<h1>Understanding DNS</h1>
Domain Name System or DNS in laymans terms is the address book for the internet. We as users remember the Fully Qualified Domain Name (FQDN) of websites such as www.google.com rather than the Internet Protocol (IP) addresses. DNS helps users in that sense: people type in the FQDN and the DNS servers resolve the IP addresses of the websites on the backend to connect us to the website. It's like remembering your friend's name in your contacts list on your phone versus remembering their phone number, it is just easier! In this tutorial, I will be showing a way to build intuition on how DNS works. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure Virtual Machines
- Microsoft Remote Desktop
- Microsoft Active Directory DNS

<h2>Steps</h2>

<h3>Create two virtual machines</h3>
First, you need to create two virtual machines: one will be the domain controller (DC-1) and the other will be a regular client (Client-1). This lab builds off of the Active Directory lab and will be setup the same way.

<p></p>

You can view the Active Directory lab [here](https://github.com/klcarpio/How-to-Install-and-use-Active-Directory).

<p></p>

Once you have your two virtual machines, log into both using Microsoft Remote Desktop. 

<p>
<img src="https://i.imgur.com/lwL9E5R.png" height="80%" width="80%" alt="1."/>
</p>
  
<p>
<img src="https://i.imgur.com/5sogtpc.png" height="80%" width="80%" alt="2."/>
</p>

<h3>Using Active Directory DNS</h3>
Next step, go into DC-1 and open up the Server Manager. Click on Tools -> DNS. Once at the DNS Manager, click on the domain (mydomain.com), right click in the main window pane and click "New Host (A or AAAA)...". Type in "mainframe" in Name and the private IP address of DC-1 (10.0.0.4) and click "OK."

<p>
<img src="https://i.imgur.com/j0fTTW6.png" height="80%" width="80%" alt="3."/>
</p>

<p>
<img src="https://i.imgur.com/7g1zAla.png" height="80%" width="80%" alt="4."/>
</p>

<p>
<img src="https://i.imgur.com/UGgpHf4.png" height="80%" width="80%" alt="5."/>
</p>

<p>
<img src="https://i.imgur.com/hDJikHB.png" height="80%" width="80%" alt="6."/>
</p>

Next, go into Client-1 and find the Command Prompt in the Start menu. In Command Prompt, type "ping mainframe". You will see that the ping results return to DC-1's private IP address. 

<p>
<img src="https://i.imgur.com/lkrTHr9.png" height="80%" width="80%" alt="7."/>
</p>

Next, go back into the DNS Manager and right click "mainframe" and click properties. Change the IP address to 8.8.8.8 and click "OK." Close Command Prompt and reopen it as an administrator. You can do this by right clicking on Command Prompt and "Run as administrator". 

<p>
<img src="https://i.imgur.com/HZ0oH2U.png" height="80%" width="80%" alt="8."/>
</p>

<p>
<img src="https://i.imgur.com/f9Z3JQY.png" height="80%" width="80%" alt="9."/>
</p>

From here, type "ipconfig /flushdns". This will flush the DNS cache and the change to mainframe should now show. Then type "ping mainframe" and it should now show mainframe's new IP address of 8.8.8.8.

<p>
<img src="https://i.imgur.com/g5jYH4d.png" height="80%" width="80%" alt="10."/>
</p>

<p>
<img src="https://i.imgur.com/SQ5iCCW.png" height="80%" width="80%" alt="11."/>
</p>

Next, we'll change a CNAME record. Go back into DC-1 and into the DNS Manager. Right click in the main window pane and click "New Alias (CNAME)..." Type in "search" in "Alias name" and for the FDQN type in Google's. 

<p>
<img src="https://i.imgur.com/g3QSZUD.png" height="80%" width="80%" alt="13"/>
</p>

<p>
<img src="https://i.imgur.com/HRVzBb1.png" height="80%" width="80%" alt="?."/>
</p>

Once this is done, go back into Client-1 and back into Command Prompt. Type in "ping search" and see the results. The ping should result to Google's IP address and FQDN. 

<p>
<img src="https://i.imgur.com/KhPn7Je.png" height="80%" width="80%" alt="14"/>
</p>

After completing this lab, you should have a basic understanding of how and what DNS is. DNS is only a small part of networking concepts and I hope that this tutorial will give you a base knowledge in this! Continue to learn and grow everyday!



**REMEMBER TO DELETE YOUR RESOURCES ONCE YOU ARE DONE WITH THE LAB!**
