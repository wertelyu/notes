# recon, CTF

### nmap

```bash
sudo nmap -A -p- -Pn 10.10.10.10 -v
-F ==> scans TOP 100 ports
-T1 ==> slows down you scanning
sudo nmap -A -F -T1 10.10.10.10 -v
```
nmap_vulners


### ffuf

```bash
ffuf -w /usr/share/wordlists/dirb/common.txt -u http://badactor.ml/FUZ -fc 403 -p 2

-fc ==> filters out the specific HTTP code in the response
-p ==> delays your requests, seconds
```

### shodan

```bash
shodan init API-key
shodan info
shodan count wordpress
shodan count wordpress 1.4.7
shodan download wordpressfile "wordpress 1.4.7"
gunzip wordpressfile.json.gz
host yahoo.comm
shodan host 98.137.11.163
---
shodan scan submit 98.137.11.163
```

### bgp.he.net

### nslookup <domain>

### whois <domain>

### theHarvestor -d <domain> -b google.com

### https://crt.sh

### wayback machine https://archive.org, https://web.atchive.org

google it --> wayback tomnomnom

[link](https://github.com/tomnomnom/waybackurls)

```bash
sudo apt install golang -y

go install github.com/tomnomnom/waybackurls@latest

cd ~/go/bin/
./waybackurls -get-versions rt-solar.ru
```

### amass

```bash
amass enum -passive -d google.com
```

### httprobe

```bash
cat urls.txt | httprobe > 
```
