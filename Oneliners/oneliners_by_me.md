**This oneliner was created by me for personal use**

### Oneliner to fuzz all hosts with wordlist using httpx and send every request to burpsuite for more investigations:- 

```httpx -l hosts -paths dir.txt -threads 100 -random-agent -x GET,POST  -tech-detect -status-code  -follow-redirects -title -http-proxy http://127.0.0.1:8080
```
