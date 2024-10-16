the page has the following js:
```
<script>
var isAdmin = false;
if (isAdmin) {
var topLinksTag = document.getElementsByClassName("top-links")[0];
var adminPanelTag = document.createElement('a');
adminPanelTag.setAttribute('href', '/admin-a1ip8n');
adminPanelTag.innerText = 'Admin panel';
topLinksTag.append(adminPanelTag);
var pTag = document.createElement('p');
pTag.innerText = '|';
topLinksTag.appendChild(pTag);
}
</script>
```

Open console and run the following: 
```
isAdmin = true;
if (isAdmin) {
var topLinksTag = document.getElementsByClassName("top-links")[0];
var adminPanelTag = document.createElement('a');
adminPanelTag.setAttribute('href', '/admin-a1ip8n');
adminPanelTag.innerText = 'Admin panel';
topLinksTag.append(adminPanelTag);
var pTag = document.createElement('p');
pTag.innerText = '|';
topLinksTag.appendChild(pTag);
}
```

klick link and delete carlos
