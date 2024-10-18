Kolla här, bra resurs från OWASP för [Testing for Special Request Header Handling](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/05-Authorization_Testing/02-Testing_for_Bypassing_Authorization_Schema)

1. vanlig request utan någon `X-Original-Url:`
2. lägg till `X-Original-Url:/hasouhasdohdouihas12` med en ogiltig path, om X-Original-Url header hanteras kommer detta resultera i en 404 
3. `X-Original-Url: /admin` kolla path för att ta bort carlos
4. testa `X-Original-Url: /admin/delete?username=carlos` men du kommer få 400 `"Missing parameter 'username'"`
5. konvertera till en post request, BAM