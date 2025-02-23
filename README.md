<!DOCTYPE html><html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Beating Heart</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(45deg, #ff9a9e, #fad0c4);
            transition: background 0.5s;
            font-size: 50px;
            overflow: hidden;
        }
        .container {
            position: relative;
            text-align: center;
        }
        .heart {
            cursor: pointer;
            animation: beat 1s infinite;
        }
        @keyframes beat {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.2);
            }
        }
        .broken {
            animation: none;
        }
        .message {
            margin-top: 20px;
            font-size: 20px;
            color: white;
            opacity: 0;
            transition: opacity 1s;
        }
        .show {
            opacity: 1;
        }
        .emoji {
            position: absolute;
            font-size: 30px;
            animation: float 5s linear infinite;
        }
        @keyframes float {
            0% { transform: translateY(100vh) scale(1); opacity: 1; }
            100% { transform: translateY(-10vh) scale(1.5); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="heart" id="heart">🖤</div>
        <div class="message" id="message">You broke my heart 💔</div>
    </div>
    <script>
        let tapCount = 0;
        const heart = document.getElementById("heart");
        const message = document.getElementById("message");
        const body = document.body;heart.addEventListener("click", () => {
        tapCount++;
        if (tapCount === 3) {
            heart.textContent = "💔";
            heart.classList.add("broken");
            document.body.style.background = "#555";
            message.classList.add("show");
        }
    });
    
    function createEmoji() {
        const emojis = ["🌸", "💮", "🌺", "🌹", "🌷", "🌻", "🌼"];
        const emoji = document.createElement("div");
        emoji.classList.add("emoji");
        emoji.textContent = emojis[Math.floor(Math.random() * emojis.length)];
        emoji.style.left = Math.random() * 100 + "vw";
        emoji.style.top = "100vh";
        emoji.style.animationDuration = (Math.random() * 3 + 3) + "s";
        document.body.appendChild(emoji);
        setTimeout(() => { emoji.remove(); }, 5000);
    }
    setInterval(createEmoji, 800);
</script>

</body>
</html>
