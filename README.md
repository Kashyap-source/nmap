# Nmap

![alt text](https://github.com/kashyap-source/nmap/blob/main/nmap.png)

**Source:** Created by  DarkStar7471 and  MuirlandOracle

***Description:***
   Get experience with Nmap, a powerful network scanning tool.
 
***Related Hosting Links***

- *TryHackMe.com*
  - Hosted currently as a free room! Recommended for beginners.
  - Link: https://tryhackme.com/room/rpnmap

***Instruction to Port Scanning:***
- When it comes to hacking, knowledge is power. The more knowledge you have about a target system or network, the more options you have available. This makes it imperative that proper enumeration is carried out before any exploitation attempts are made.
- Say we have been given an IP (or multiple IP addresses) to perform a security audit on. Before we do anything else, we need to get an idea of the “landscape” we are attacking. What this means is that we need to establish which services are running on the targets. For example, perhaps one of them is running a webserver, and another is acting as a Windows Active Directory Domain Controller. The first stage in establishing this “map” of the landscape is something called port scanning. When a computer runs a network service, it opens a networking construct called a “port” to receive the connection.  Ports are necessary for making multiple network requests or having multiple services available. For example, when you load several webpages at once in a web browser, the program must have some way of determining which tab is loading which web page. This is done by establishing connections to the remote webservers using different ports on your local machine. Equally, if you want a server to be able to run more than one service (for example, perhaps you want your webserver to run both HTTP and HTTPS versions of the site), then you need some way to direct the traffic to the appropriate service. Once again, ports are the solution to this. Network connections are made between two ports – an open port listening on the server and a randomly selected port on your own computer. For example, when you connect to a web page, your computer may open port 49534 to connect to the server’s port 443.

![alt text](https://github.com/kashyap-source/nmap/blob/main/ima/3XAfRpI.png) 

- As in the previous example, the diagram shows what happens when you connect to numerous websites at the same time. Your computer opens up a different, high-numbered port (at random), which it uses for all its communications with the remote server.

- Every computer has a total of 65535 available ports; however, many of these are registered as standard ports. For example, a HTTP Webservice can nearly always be found on port 80 of the server. A HTTPS Webservice can be found on port 443. Windows NETBIOS can be found on port 139 and SMB can be found on port 445. It is important to note; however, that especially in a CTF setting, it is not unheard of for even these standard ports to be altered, making it even more imperative that we perform appropriate enumeration on the target.

- If we do not know which of these ports a server has open, then we do not have a hope of successfully attacking the target; thus, it is crucial that we begin any attack with a port scan. This can be accomplished in a variety of ways – usually using a tool called nmap, which is the focus of this room. Nmap can be used to perform many different kinds of port scan – the most common these will be introduced in upcoming tasks; however, the basic theory is this: nmap will connect to each port of the target in turn. Depending on how the port responds, it can be determined as being open, closed, or filtered (usually by a firewall). Once we know which ports are open, we can then look at enumerating which services are running on each port – either manually, or more commonly using nmap.

- So, why nmap? The short answer is that its currently the industry standard for a reason: no other port scanning tool comes close to matching its functionality (although some newcomers are now matching it for speed). It is an extremely powerful tool – made even more powerful by its scripting engine

- which can be used to scan for vulnerabilities, and in some cases even perform the exploit directly! Once again, this will be covered more in upcoming tasks.

- For now, it is important that you understand: what port scanning is; why it is necessary; and that nmap is the tool of choice for any kind of initial enumeration.

**Task 1**
 1) What networking constructs are used to direct traffic to the right application on a server?
     **ports**

 2) How many of these are available on any network-enabled computer?
    **65535**

 3) [Research] How many of these are considered "well-known"? (These are the "standard" numbers mentioned in the task)
     **1024**

**Task 2**
- Deploy the attached machine and give it a few minutes to properly start up

**Task 3 (Nmap Quiz)**
- Nmap is installed by default on Kali Linux or install it by command "sudo apt-get install nmap" in termial
- It can be accessed by typing nmap in a terminal, followed by some of the switches which will be covered below.
-For help menu (accessed with nmap --help).Include all parts of the switch unless otherwise specified, this includes the hyphen at the start (-).

 1) First, how do you access the help menu?
     **-h**
     
 2) Often referred to as a stealth scan, what is the first switch listed for a 'Syn Scan'?
     **-sS**
     
 3) Not quite as useful but how about a 'UDP Scan'?
    **-sU**

 4) What about operating system detection?
     **-O**
     
 5) How about service version detection? 
     **-sV** 
     
 6) Most people like to see some output to know that their scan is actually doing things, what is the verbosity flag?
     **-v**
     
 7) What about 'very verbose'? (A personal favorite)
     **-vv**
    
 8) Sometimes saving output in a common document format can be really handy for reporting, how do we save output in xml format?
     **-oX**

 9) Aggressive scans can be nice when other scans just aren't getting the output that you want and you really don't care how 'loud' you are, what is the switch for enabling this? 
     **-A**

 10) How do I set the timing to the max level, sometimes called 'Insane'?
      **-T5**

 11) What about if I want to scan a specific port?
      **-p**

 12) How about if I want to scan every port?
      **-p-**

 13) What if I want to enable using a script from the nmap scripting engine? For this, just include the first part of the switch without the specification of what script to run.
      **--script**

 14) What if I want to run all scripts out of the vulnerability category? 
      **--script vuln**

 15) What switch should I include if I don't want to ping the host?
      **-Pn**

**Task 4 (Nmap Scanning)**
 1) Let's go ahead and start with the basics and perform a syn scan on the box provided. What will this command be without the host IP address?
    
    **nmap -sS or sudo nmap -sS**

![alt text](https://github.com/kashyap-source/nmap/blob/main/ima/Screenshot_2020-08-31_02-11-14.png) 

 2) After scanning this, how many ports do we find open under 1000?
      **2**

 3) What communication protocol is given for these ports following the port number?
      **tcp**

 4) Perform a service version detection scan, what is the version of the software running on port 22?
      **6.6.1p1**

![alt text](https://github.com/kashyap-source/nmap/blob/main/ima/Screenshot%202020-11-04%2010_13_04.png) 

 5) Perform an aggressive scan, what flag isn't set under the results for port 80?
      **httponly**
    
    **command**
         
          nmap -vv -A <BOX_IP>
![alt text](https://github.com/kashyap-source/nmap/blob/main/ima/Screenshot%202020-11-04%2013_46_50.png) 

 6) Perform a script scan of vulnerabilities associated with this box, what denial of service (DOS) attack is this box susceptible to? Answer with the name for the vulnerability that is given as the section title in the scan output. A vuln scan can take a while to complete. In case you get stuck, the answer for this question has been provided in the hint, however, it's good to still run this scan and get used to using it as it can be invaluable. 
**http-slowloris-check**

  

   




