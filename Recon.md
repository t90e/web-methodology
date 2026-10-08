# App Recon and analysis


## Passive methods

### Map visible content

Manual browsing of the website, may discover technology used

eg. "Powered by..." "About this site"

potential credit to web developer with seperate site identifying technology.

Visit /robots.txt , find folders or interest or technology, 

print with; curl -s http://192.168.1.100/robots.txt | grep "Disallow"

download with; wget http://192.168.1.100/robots.txt

### Examine banners
Wireshark traffic capture, examine HTTP packets.

### 3rd party scanners 

https://sitereport.netcraft.com/

https://whatcms.org/

https://www.wappalyzer.com/

https://securityheaders.com/

## Active methods

### Examine banners 
Netcat

### Nmap scans
scan for top 1000 ports

sudo nmap -sV -sS 192.168.1.100 

scan for HTTP headers

nmap 192.168.1.100 -p80,443 --script=http-headers

nmap 192.168.1.100 -p80,443 --script=http-methods

### Discover hidden & default content (Direcory/File Bruteforce)


### Test for debug parameters


### Identify data entry points (Discover Dynamic Content in Burp Pro)


### Research existing vulnerabilitties in technology
https://www.exploit-db.com/ 

https://nvd.nist.gov/

look for exploits matching known running versions, some exploits may have prerequiests or misconfigurations.

### Gather wordlists for specific techniology (Assetnote ones are excellent)
https://www.kali.org/tools/dirb/

dirb http://192.168.1.100/

### Map the attack surface automatically
https://github.com/jaeles-project/gospider

gospider -s “http://192.168.1.100"

if login page, get PHPSESSID cookie from web dev tools 

gospider -s “http://192.168.1.100/WackoPicko” --cookie “PHPSESSID=[COOKIE]"


### Identify javascript files
https://github.com/hakluke/hakrawler

echo https://google.com | hakrawler -subs

within the javascript files
https://github.com/GerbenJavado/LinkFinder

https://deobfuscate.io/




