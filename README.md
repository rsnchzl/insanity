# Insanity 
Solving Vulnhub's Insanity  machine

<div>
  <h2>Index</h2>
  <h5>1. Introduction<h5>
  <h5>2. Installation and setup</h5>
  <h5>3. Solving the machine</h5>
  <h5>4. Conclusion</h5>
</div>

<div>
  <h2>1. Introduction</h2>
 This vulnerable Vulnhub machine presents similar difficulty to ewpt certification. Ideal to prepare the ewpt.
  <div>
  <h2>2. Installation and setup</h2>
  

  First, we need to install the ova file available [here](https://www.vulnhub.com/entry/insanity-1,536/). When we have the .ova file we just need to open it to import it into VirtualBox, VMware or your favourite platform.  Once imported we must make sure that the network adapter is in bridge mode. Now we can start with the enumeration phase.
 <h2>  3. Solving the machine</h2>
 The first thing to do is to identify the IP of the victim machine, for this we can play with "arp-scan --localnet --ignoredups", this will identify the IP addresses assigned in your local network (thanks to the --localnet parameter).<br/>
  <img src="https://github.com/rsnchzl/insanity/blob/main/screenshots/arpscan.png"/> <br/>
  <br/>
  Once we have identified the IP address of the victim machine, we will launch a ping -c 1 "ip-victim-machine" to check if we receive a response, and also to identify the operating system of the victim machine thanks to the ttl.<br/>
  <img src="https://github.com/rsnchzl/insanity/blob/main/screenshots/ping.png"/> <br/>
  <br/>
  Well, now we know that the ttl of the victim machine is 64, so most likely the operating system of the victim machine is Linux. 
 The next step will be to scan the ports of the ip of the victim machine to detect the services that are running behind, for this we will use the nmap tool and indicate with -p- that we want to scan all existing ports (65535) on the ip address of the victim machine.

  <img src="https://github.com/rsnchzl/insanity/blob/main/screenshots/nmap1.png"/> <br/>
  <br/>
    We will also launch some basic reconnaissance scripts to detect the versions of the services that are running in addition to other data, for this we will use nmap again with the -sCV parameter on ports 21, 22 and 80.
  <img src="https://github.com/rsnchzl/insanity/blob/main/screenshots/nmapscv.png"/> <br/> 
  <br/>
  If we look at the result it informs us that one of the scripts launched, ftp-anon reports that the Anonymous user is enabled and therefore we could connect through FTP. So let's try to connect via FTP.
  <img src="https://github.com/rsnchzl/insanity/blob/main/screenshots/ftpconnect.png"/> <br/>
  <br/>
  Upon investigation we discovered that there is an empty directory called "pub" and we also discovered that we have no privileges to upload any files, so for the moment we will leave the ftp connection aside.
Now we will focus on port 80 and we will access through a browser to the http service where we will be able to see a server sales web page. In the header of the web we can see a contact email called hello@insanityhosting.vm which makes us think that if we are applying virtual hosting insanityhosting.vm could be a domain, therefore we will reference it in the file /etc/hosts as follows:
<img src="https://github.com/rsnchzl/insanity/blob/main/screenshots/etchosts.png"/> <br/>
<br/>
  It's time to discover routes in the web, for this we will use gobuster together with the Seclists 2.3 medium dictionary.
  <img src="https://github.com/rsnchzl/insanity/blob/main/screenshots/gobuster1.png"/> <br/>
  <br/>
  
Well, let's start investigating, if we access the news directory we will see that there is a possible username called "Otis" and if we access the webmail directory we will see a SquirrelMail login. We know that very probablente Otis is a user, but we do not know his password therefore we will play with Hydra with the dictionary rockyou to make an attack of brute force through the method POST to try to decipher the password.
<img src="https://github.com/rsnchzl/insanity/blob/main/screenshots/hydra1.png"/> <br/>
<br/>
Well, brute force attack successful thanks to the very secure password (123456) of the user Otis (note the irony), so we can now access SquirrelMail but we don't see anything interesting. Instead if we access the path previously discovered by Gobuster called monitoring we see another login where Otis' credentials are reused so we can log in. 
  
  

  
  


