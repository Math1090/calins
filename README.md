<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Simulateur de câlins</title>
  <style>
    body {
      background: linear-gradient(135deg, #ffe0ec, #ffe6fa);
      font-family: 'Comic Sans MS', cursive, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      margin: 0;
      padding: 20px;
    }
    h1 {
      color: #ff4081;
      text-shadow: 1px 1px #fff;
    }
    button {
      background-color: #ff91c2;
      border: none;
      border-radius: 20px;
      padding: 15px 30px;
      margin: 10px;
      font-size: 1.2em;
      cursor: pointer;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
      transition: transform 0.1s;
    }
    button:hover {
      transform: scale(1.05);
    }
    .floating-heart {
      position: fixed;
      font-size: 30px;
      animation: float 2s ease-out forwards;
    }
    @keyframes float {
      0% {opacity: 1; bottom: 50px;}
      100% {opacity: 0; bottom: 300px;}
    }
  </style>
</head>
<body>
  <h1>Simulateur de câlins 🧸</h1>
  <div id="buttons">
    <button onclick="sendLove('Fais moi un câlin')">Fais moi un câlin 🤗</button>
    <button onclick="sendLove('J\'ai faim')">J'ai faim 🍽️</button>
    <button onclick="sendLove('Je t\'aime')">Je t'aime ❤️</button>
    <button onclick="sendLove('Tu peux faire le dîner ?')">Tu peux faire le dîner ? 🍳</button>
    <button onclick="sendLove('Resto ?')">Resto ? 🍝</button>
    <button onclick="sendLove('On regarde une vidéo ?')">On regarde une vidéo ? 🎬</button>
    <button onclick="sendLove('Envoie-moi un mot doux')">Envoie-moi un mot doux 💌</button>
  </div>

  <script>
    function sendLove(message) {
      showHeart();

      // EmailJS (à connecter avec ton compte EmailJS)
      emailjs.send("default_service", "template_test", {
        message: message,
        to_email: "mathhotel2015@gmail.com"
      });

      // Discord Webhook (à remplacer par ton vrai webhook)
      fetch("https://discord.com/api/webhooks/TON_WEBHOOK_ID", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify({ content: `📩 **${message}** de ta copine 💕` })
      });
    }

    function showHeart() {
      const heart = document.createElement("div");
      heart.className = "floating-heart";
      heart.style.left = Math.random() * 90 + "%";
      heart.innerText = "💖";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 2000);
    }
  </script>

  <!-- EmailJS SDK -->
  <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
  <script>
    (function() {
      emailjs.init("YOUR_PUBLIC_KEY"); // Remplace avec ta clé publique EmailJS
    })();
  </script>
</body>
</html>
