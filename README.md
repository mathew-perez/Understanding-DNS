![image](https://github.com/mathew-perez/Understanding-DNS/assets/144407220/15d4de3a-038e-409f-9fa6-0c33010dd0a8)


<h1>Understanding DNS</h1>
Domain Name System (DNS) is the phonebook of the Internet. DNS translates domain names to IP addresses and DNS servers eliminate the need for humans to memorize IP addresses. Users only need to know the name of a website instead of typing out complicate numeric or alpha-numeric IP adresses. This tutorial will build intuition on how DNS works. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure Virtual Machines
- Microsoft Remote Desktop
- Microsoft Active Directory DNS

<h2>Steps</h2>

<h3>Create two virtual machines</h3>
First, you need to create two virtual machines: one will be a virtual machine running windows server (DC-1) and the other will be running windows 10 (Client-1). This lab builds off of the Active Directory lab and will be setup the same way.

<p></p>

You can view the Active Directory lab [here](https://github.com/mathew-perez/configure-ad).

<p></p>

Then log into both virtual machines using Microsoft Remote Desktop. 


<h3>Using Active Directory DNS</h3>
Next step, go into DC-1 and open up the Server Manager. Click on Tools -> DNS. Once at the DNS Manager, click on the domain (mydomain.com), right click in the main window pane and click "New Host (A or AAAA)...". Type in "mainframe" in Name and the private IP address of DC-1 (10.0.0.4) and click "OK."

![image](https://github.com/mathew-perez/Understanding-DNS/assets/144407220/be2858ad-7ad6-484e-9dbb-9cae3dfed54b)

</p>

Next, go into Client-1 and find the Command Prompt in the Start menu. In Command Prompt, type "ping mainframe". You will see that the ping results return to DC-1's private IP address. 

![image](https://github.com/mathew-perez/Understanding-DNS/assets/144407220/eab46956-ade3-44f5-bf48-c3ebb485319d)


Next, go back into the DNS Manager and right click "mainframe" and click properties. Change the IP address to 8.8.8.8 and click "OK." Close Command Prompt and reopen it as an administrator. You can do this by right clicking on Command Prompt and "Run as administrator". 

![image](https://github.com/mathew-perez/Understanding-DNS/assets/144407220/5b758507-b53a-4a66-9cb9-ef9dd4b8befc)


From here, type "ipconfig /flushdns". This will flush the DNS cache and the change to mainframe should now show. Then type "ping mainframe" and it should now show mainframe's new IP address of 8.8.8.8.

![image](https://github.com/mathew-perez/Understanding-DNS/assets/144407220/9a0daa27-1f20-41a0-b785-4bb4dbeb1cfd)


Next, we'll change a CNAME record. Go back into DC-1 and into the DNS Manager. Right click in the main window pane and click "New Alias (CNAME)..." Type in "search" in "Alias name" and for the FDQN type in Google's. 

![image](https://github.com/mathew-perez/Understanding-DNS/assets/144407220/ea4becda-1bce-4a0b-be0d-74ea0e273125)


Once this is done, go back into Client-1 and back into Command Prompt. Type in "ping search" and see the results. The ping should result to Google's IP address and FQDN. 

![image](https://github.com/mathew-perez/Understanding-DNS/assets/144407220/9ec80441-c965-4c67-b693-6cd9ef8fcf1e)


After completing this lab, you should have a basic understanding of what DNS is and how is works.
