<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>aopa</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: radial-gradient(ellipse at center, #000000, #0a0a0a, #111111);
      height: 100vh;
      overflow: hidden;
      position: relative;
      font-family: 'Brush Script MT', cursive;
    }

    #startBtn {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      padding: 20px 60px;
      font-size: 30px;
      font-weight: bold;
      color: #fff;
      background: linear-gradient(135deg, #ff0080, #7928ca);
      border: none;
      border-radius: 15px;
      cursor: pointer;
      z-index: 1000;
      box-shadow: 0 0 30px #ff00cc88;
      animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
      0% { box-shadow: 0 0 10px #ff00cc88; }
      50% { box-shadow: 0 0 25px #ff00ccff; }
      100% { box-shadow: 0 0 10px #ff00cc88; }
    }

    .loveText {
      position: absolute;
      color: #ff99cc;
      font-weight: bold;
      user-select: none;
      pointer-events: none;
      font-size: 24px;
      text-shadow: 0 0 10px #ff66cc, 0 0 20px #ff99cc;
      animation: floatUp 5s ease-out forwards;
      white-space: nowrap;
    }

    @keyframes floatUp {
      0% {
        opacity: 0;
        transform: translateY(30px) scale(0.9) rotate(0deg);
      }
      20% {
        opacity: 1;
      }
      100% {
        opacity: 0;
        transform: translateY(-150px) scale(1.2) rotate(20deg);
      }
    }

    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background: #ff66cc;
      transform: rotate(45deg);
      animation: floatHeart 6s ease-in-out infinite;
    }

    .heart::before,
    .heart::after {
      content: "";
      position: absolute;
      width: 20px;
      height: 20px;
      background: #ff66cc;
      border-radius: 50%;
    }

    .heart::before {
      top: -10px;
      left: 0;
    }

    .heart::after {
      top: 0;
      left: -10px;
    }

    @keyframes floatHeart {
      0% {
        transform: translateY(0) rotate(45deg);
        opacity: 1;
      }
      100% {
        transform: translateY(-200px) rotate(45deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

<button id="startBtn">INICIAR A MAGIA</button>

<!-- Música ambiente -->
<audio id="bgMusic" src="https://cdn.pixabay.com/audio/2022/03/15/audio_8cfa2ce69b.mp3" loop></audio>

<script>
  const btn = document.getElementById('startBtn');
  const music = document.getElementById('bgMusic');

  btn.addEventListener('click', () => {
    btn.remove();
    music.play();

    // Mensagens infinitas de amor
    setInterval(() => {
      const love = document.createElement('div');
      love.textContent = 'eu te amo, anjs ❤️';
      love.classList.add('loveText');

      // Posição aleatória
      love.style.left = Math.random() * (window.innerWidth - 200) + 'px';
      love.style.top = Math.random() * window.innerHeight + 'px';
      love.style.fontSize = 18 + Math.random() * 24 + 'px';

      document.body.appendChild(love);

      setTimeout(() => love.remove(), 5000);
    }, 160);

    // Corações mágicos flutuando
    setInterval(() => {
      const heart = document.createElement('div');
      heart.classList.add('heart');
      heart.style.left = Math.random() * window.innerWidth + 'px';
      heart.style.top = window.innerHeight + 'px';
      heart.style.animationDuration = (4 + Math.random() * 4) + 's';
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 6000);
    }, 300);
  });
</script>

</body>
</html>
