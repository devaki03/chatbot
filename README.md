<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pink Chatbot</title>

    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: #ffc0cb;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 10px 0;
        }

        .chat-container {
            width: 100%;
            max-width: 400px;
            height: 500px; /* Much shorter - fixed height */
            background: #fff0f5;
            border-radius: 15px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.2);
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        .chat-header {
            background: linear-gradient(135deg, #ff69b4, #ffb6c1);
            color: white;
            padding: 12px 16px;
            text-align: center;
            font-size: 16px;
            font-weight: bold;
            border-radius: 15px 15px 0 0;
        }

        .chat-box {
            flex: 1;
            padding: 12px;
            overflow-y: auto;
            min-height: 200px; /* Minimum height for chat area */
        }

        .message {
            max-width: 75%;
            margin: 6px 0;
            padding: 8px 12px;
            border-radius: 15px;
            font-size: 13px;
        }

        .user {
            background: #ff69b4;
            color: white;
            align-self: flex-end;
        }

        .bot {
            background: #ffe4e1;
            align-self: flex-start;
        }

        .input-box {
            display: flex;
            border-top: 1px solid #ddd;
            background: #fff;
            padding: 4px;
        }

        input {
            flex: 1;
            padding: 10px;
            border: none;
            outline: none;
            font-size: 13px;
        }

        button {
            padding: 10px 16px;
            background: #c8a2c8;
            color: white;
            border: none;
            cursor: pointer;
            font-weight: bold;
        }

        button:hover {
            background: #b57edc;
        }
    </style>
</head>

<body>

<div class="chat-container">
    <div class="chat-header">💕 Pink Chatbot 💕</div>
    <div class="chat-box" id="chatBox"></div>

    <div class="input-box">
        <input type="text" id="userInput" placeholder="Type a message..." onkeypress="handleKeyPress(event)">
        <button onclick="sendMessage()">Send</button>
    </div>
</div>

<script>
function sendMessage() {
    let input = document.getElementById("userInput");
    let msg = input.value.trim();

    if (msg === "") return;

    let chatBox = document.getElementById("chatBox");

    // User message
    let userMsg = document.createElement("div");
    userMsg.className = "message user";
    userMsg.innerText = msg;
    chatBox.appendChild(userMsg);

    // Bot typing effect
    let botMsg = document.createElement("div");
    botMsg.className = "message bot";
    botMsg.innerText = "Typing...";
    chatBox.appendChild(botMsg);

    chatBox.scrollTop = chatBox.scrollHeight;

    setTimeout(() => {
        botMsg.innerText = getReply(msg);
        chatBox.scrollTop = chatBox.scrollHeight;
    }, 500);

    input.value = "";
}

function getReply(msg) {
    msg = msg.toLowerCase();

    if (msg.includes("hello") || msg.includes("hi")) 
        return "Hey there 💗 How can I help you?";

    if (msg.includes("how are you")) 
        return "I'm doing amazing 😄 What about you?";

    if (msg.includes("name")) 
        return "I'm your pink chatbot 🌸";

    if (msg.includes("help")) 
        return "Tell me what you need, I'll try my best! 💖";

    if (msg.includes("bye")) 
        return "Bye 👋 Take care 💜";

    if (msg.includes("thank")) 
        return "You're welcome 😊";

    return "Hmm 🤔 I didn't understand that. Try something else! 💕";
}

function handleKeyPress(event) {
    if (event.key === "Enter") {
        sendMessage();
    }
}
</script>

</body>
</html>
