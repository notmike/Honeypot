# Honeypot

I implemented a [Modern Honey Network](https://github.com/threatstream/mhn) with 6 different honeypots on Ubuntu 14.04 x64 Digitalocean droplets. The honeypots started receiving attacks immediately. After only 48 hours, my honey network had received over 6,000 attacks.

Here is the complete data collection from the honeypots (for your casual reading) : [session.json](https://raw.githubusercontent.com/notmike/Honeypot/master/assets/session.json)

Here is a list of the honeypots I used on my honey network:

+ Honeypot 0 - [Dionaea](https://www.edgis-security.org/single-post/dionaea-malware-honeypot)
+ Honeypot 1 - [Kippo](https://github.com/desaster/kippo)
+ Honeypot 2 - [Shockpot Sinkhole](https://github.com/threatstream/shockpot)
+ Honeypot 3 - [p0f](http://lcamtuf.coredump.cx/p0f3/)
+ Honeypot 4 - [Snort](https://www.snort.org/)
+ Honeypot 5 - [Glastopf](https://github.com/mushorg/glastopf)

Most honeypots were straight forward during setup, and seemed to get attacked almost immediately. The only exception to that was my last honeypot which was running Glastopf. I tried to troubleshoot it to make sure it was running correctly and it seemed to be fine. I ran sqlmap against multiple injection points but no attacks registered on the MHN Admin server.

### MHN Admin Server - Walkthrough

![](https://raw.githubusercontent.com/notmike/Honeypot/master/assets/mhn_admin_site.gif)

### Attack Stats (most recent 24 hours)

![](https://raw.githubusercontent.com/notmike/Honeypot/master/assets/dashboard.png)

Here I've listed the function of the most frequently attacked ports:

| Attacked Ports        | Common Use     |
| --------------------- | -------------- |
| 22                    | SSH            |
| 5060                  | VoIP           |
| 25                    | SMTP           |
| 445                   | Windows Server |
| 3306                  | MySQL          |

### Active Honeypots

![](https://raw.githubusercontent.com/notmike/Honeypot/master/assets/sensors.png)

### Kippo Honeypot Charts

![](https://raw.githubusercontent.com/notmike/Honeypot/master/assets/kippo_pws.png)

It appears that many of these bots are really only interested in the lowest hanging fruit, given the #1 SSH username *AND* password attempt was "support".

![](https://raw.githubusercontent.com/notmike/Honeypot/master/assets/kippo_attackers.png)

I was curious as to which countries were responsible for the attempts at brute-forcing ssh on the Kippo honeypot...

| Attacker IPs    | Country   |
| --------------  | --------- |
| 91.134.213.144  | Bulgaria  |
| 198.24.171.250  | USA       |
| 195.154.105.200 | France    |
| 46.101.178.128  | Germany   |
| 150.95.146.205  | Japan     |
