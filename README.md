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
</div>
