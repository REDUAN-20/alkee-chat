<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Palkee Chat</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f2f2f2;
      padding: 20px;
    }
    #chat-box {
      background: white;
      padding: 10px;
      height: 300px;
      overflow-y: scroll;
      border: 1px solid #ccc;
      margin-bottom: 10px;
    }
    #message {
      width: 75%;
      padding: 10px;
      font-size: 16px;
    }
    #send {
      padding: 10px 20px;
      font-size: 16px;
      background: #28a745;
      color: white;
      border: none;
      cursor: pointer;
    }
    #send:hover {
      background: #218838;
    }
  </style>
</head>
<body>
  <h2>Palkee Chat</h2>
  <div id="chat-box"></div>
  <input type="text" id="message" placeholder="Type your message..." />
  <button id="send">Send</button>

  <script>
    const chatBox = document.getElementById('chat-box');
    const messageInput = document.getElementById('message');
    const sendButton = document.getElementById('send');

    function appendMessage(text, sender = "You") {
      const msgDiv = document.createElement('div');
      msgDiv.textContent = sender + ": " + text;
      chatBox.appendChild(msgDiv);
      chatBox.scrollTop = chatBox.scrollHeight;
    }

    sendButton.addEventListener('click', () => {
      const msg = messageInput.value.trim();
      if (msg) {
        appendMessage(msg);
        setTimeout(() => {
          appendMessage("Got it! (Palkee)", "Palkee");
        }, 1000);
        messageInput.value = "";
      }
    });

    messageInput.addEventListener('keydown', (e) => {
      if (e.key === 'Enter') {
        sendButton.click();
      }
    });
  </script>
</body>
</html>
