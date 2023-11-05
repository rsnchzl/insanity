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
  
</div>
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
</div>
