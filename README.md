
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy New Year Shilpa</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      height: 100vh;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      background: radial-gradient(circle, #ff7eb3, #ff758c, #ff5a65);
      background-size: 400% 400%;
      animation: bgAnimation 10s ease infinite;
      font-family: 'Arial', sans-serif;
    }

    @keyframes bgAnimation {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    .content {
      text-align: center;
      color: white;
    }

    h1 {
      font-size: 4rem;
      margin: 0;
      letter-spacing: 5px;
      text-transform: uppercase;
      animation: glowText 2s infinite alternate;
    }

    h2 {
      font-size: 2rem;
      margin-top: 10px;
      letter-spacing: 3px;
      color: #fff8dc;
    }

    @keyframes glowText {
      from {
        text-shadow: 0 0 5px #ff69b4, 0 0 10px #ff69b4, 0 0 20px #ff69b4, 0 0 30px #ff69b4;
      }
      to {
        text-shadow: 0 0 10px #ff1493, 0 0 20px #ff1493, 0 0 30px #ff1493, 0 0 50px #ff1493;
      }
    }

    canvas {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
    }
  </style>
</head>
<body>
  <div class="content">
    <h1>💐Happy New Year💐</h1>
    <h2>❤️To My Dearest Shilpa❤️</h2>
  </div>
  <canvas id="confettiCanvas"></canvas>

  <script>
    const canvas = document.getElementById('confettiCanvas');
    const ctx = canvas.getContext('2d');
    const resizeCanvas = () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    };
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    const confetti = [];
    const colors = ['#FF5733', '#FFC300', '#DAF7A6', '#FF69B4', '#6495ED'];

    for (let i = 0; i < 150; i++) {
      confetti.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        size: Math.random() * 8 + 2,
        color: colors[Math.floor(Math.random() * colors.length)],
        dx: (Math.random() - 0.5) * 4,
        dy: Math.random() * 5 + 1,
        rotation: Math.rand });
    }

    const drawConfetti = () => {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      confetti.forEach(c => {
        ctx.save();
        ctx.translate(c.x, c.y);
        ctx.rotate((c.rotation * Math.PI) / 180);
        ctx.fillStyle = c.color;
        ctx.fillRect(-c.size / 2, -c.size / 2, c.size, c.size);
        ctx.restore();
        c.x += c.dx;
        c.y += c.dy;
        c.rotation += c.dy;

        if (c.x > canvas.width) c.x = 0;
        if (c.x < 0) c.x = canvas.width;
        if (c.y > canvas.height) c.y = 0;
      });
    };

    const animate = () => {
      drawConfetti();
      requestAnimationFrame(animate);
    };
    animate();
  </script>
</body>
</html>
