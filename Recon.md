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

HTTP headers / methods:

nmap 192.168.1.100 -p80,443 --script=http-headers

nmap 192.168.1.100 -p80,443 --script=http-methods

### Discover hidden & default content (Direcory/File Bruteforce)

worldist with dirb https://www.kali.org/tools/dirb/

dirb http://192.168.1.100/ /usr/share/wordlists/dirb/common.txt

gobuster dir -u http://192.168.1.100/ -w wordlist.txt

### Test for debug parameters

?debug=1, ?debug=true, ?test=1, ?dev=1, ?verbose=1, ?trace=1 appended to URLs

feed malformed input (bad types, SQL chars, oversized values) into forms/params and see if the app returns a raw stack trace

### Identify data entry points

burp suite live passive crawl identifies automatically 

js file - AJAX endpoints and params are often only referenced in JS

repeat as diffrent levels of auth if possible (guest, user, admin)

### Research existing vulnerabilitties in technology

https://www.exploit-db.com/ 

https://nvd.nist.gov/

look for exploits matching known running versions, some exploits may have prerequiests or misconfigurations.

### Map the attack surface automatically

https://github.com/jaeles-project/gospider

gospider -s “http://192.168.1.100"

if login page, get PHPSESSID cookie from web dev tools 

gospider -s “http://192.168.1.100/WackoPicko” --cookie “PHPSESSID=[COOKIE]"

burp suite live passive crawl also creates site map.

### Identify javascript files

https://github.com/hakluke/hakrawler

echo 192.168.1.100 | hakrawler -subs

within the javascript files

https://github.com/GerbenJavado/LinkFinder

Analyze JS for endpoints/secrets with LinkFinder, deobfuscate with 

https://deobfuscate.io/




