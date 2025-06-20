<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Eu Te Amo 💖</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: black;
      color: pink;
      font-family: 'Courier New', Courier, monospace;
    }
    canvas {
      display: block;
    }
    #love {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 4em;
      color: red;
      text-shadow: 0 0 20px white;
      display: none;
      animation: pulse 1s infinite alternate;
    }
    @keyframes pulse {
      from { transform: translate(-50%, -50%) scale(1); }
      to { transform: translate(-50%, -50%) scale(1.2); }
    }
  </style>
</head>
<body>
  <canvas id="matrix"></canvas>
  <div id="love">EU TE AMO ❤️</div>

  <script>
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');
    canvas.height = window.innerHeight;
    canvas.width = window.innerWidth;
    const hearts = "💖💕💘💝❤️🩷💓💞💗".split('');
    const fontSize = 20;
    const columns = canvas.width / fontSize;
    const drops = Array.from({length: columns}, () => 1);
    function draw() {
      ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = "pink";
      ctx.font = fontSize + "px monospace";
      for (let i = 0; i < drops.length; i++) {
        const text = hearts[Math.floor(Math.random() * hearts.length)];
        ctx.fillText(text, i * fontSize, drops[i] * fontSize);
        if (drops[i] * fontSize > canvas.height && Math.random() > 0.975)
          drops[i] = 0;
        drops[i]++;
      }
    }
    let interval = setInterval(draw, 50);
    setTimeout(() => {
      clearInterval(interval);
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      document.getElementById('love').style.display = 'block';
    }, 10000);
  </script>
</body>
</html>
