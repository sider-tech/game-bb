<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>You’ve Unlocked My Heart 💘</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      width: 100vw;
      height: 100vh;
      font-family: 'Comic Sans MS', cursive;
      background: linear-gradient(to bottom right, #ffafbd, #ffc3a0);
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .phone-frame {
      width: 360px;
      height: 640px;
      background: #fff;
      border: 12px solid #333;
      border-radius: 30px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
      overflow: hidden;
      position: relative;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      background: linear-gradient(to bottom right, #ffafbd, #ffc3a0);
    }

    h1 {
      font-size: 1.5rem;
      color: #fff;
      margin-bottom: 10px;
    }

    .heart {
      width: 40px;
      height: 40px;
      background-color: red;
      position: absolute;
      clip-path: polygon(50% 0%, 100% 35%, 85% 100%, 50% 75%, 15% 100%, 0% 35%);
      animation: float 5s infinite;
      cursor: pointer;
      z-index: 2;
    }

    @keyframes float {
      0% { transform: translateY(0); }
      50% { transform: translateY(-20px); }
      100% { transform: translateY(0); }
    }

    .message {
      display: none;
      font-size: 1rem;
      color: white;
      max-width: 90%;
      margin: 10px auto;
      z-index: 3;
    }

    #finalMessage {
      display: none;
      font-size: 1.2rem;
      color: white;
      margin-top: 15px;
      z-index: 3;
    }

    #girl {
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      width: 80px;
      animation: bounce 1s infinite;
      z-index: 1;
    }

    @keyframes bounce {
      0%, 100% { transform: translateX(-50%) translateY(0); }
      50% { transform: translateX(-50%) translateY(-10px); }
    }
  </style>
</head>
<body>
  <div class="phone-frame">
    <h1>Collect All The Hearts 💖</h1>
    <div id="messages" class="message"></div>
    <div id="finalMessage">Mera pyara sa Bugga 💘<br><strong>I love you forever 💖</strong></div>
    <img id="girl" src="https://cdn-icons-png.flaticon.com/512/3048/3048122.png" alt="Cute Girl">
  </div>

  <script>
    const messages = [
      "Pooja, you’re the reason I smile every day 😊",
      "Every memory with you is my favorite.",
      "Your love is my strength and my peace.",
      "You're the light in my life, brighter than any star.",
      "Every moment spent with you is a blessing.",
      "You make my heart feel full and complete.",
      "You are my sunshine on cloudy days ☀️",
      "I never believed in forever—until I met you.",
      "My heart chose you and only you ❤️",
      "Mera pyara sa Bugga"
    ];

    let collected = 0;

    function createHeart() {
      const heart = document.createElement('div');
      heart.classList.add('heart');
      const phone = document.querySelector('.phone-frame');
      const phoneRect = phone.getBoundingClientRect();
      const left = Math.random() * (phone.clientWidth - 40);
      const top = Math.random() * (phone.clientHeight - 80);
      heart.style.left = left + 'px';
      heart.style.top = top + 'px';

      heart.addEventListener('click', () => {
        heart.remove();
        if (collected < messages.length) {
          document.getElementById('messages').style.display = 'block';
          document.getElementById('messages').innerText = messages[collected];
          collected++;
          if (collected === messages.length) {
            document.getElementById('finalMessage').style.display = 'block';
          }
        }
        spawnHearts();
      });

      phone.appendChild(heart);
    }

    function spawnHearts(count = 3) {
      for (let i = 0; i < count; i++) {
        createHeart();
      }
    }

    spawnHearts();
  </script>
</body>
</html>
