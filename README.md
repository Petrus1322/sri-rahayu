# sri-rahayu
LOVEEEEUUUUSOOOOMUUUUUCH
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Hati Rahayu</title>
  <style>
    body {
      background: black;
      color: #00ff99;
      font-family: monospace;
      white-space: pre;
      text-align: center;
      font-size: 12px;
      line-height: 12px;
    }
    #heart {
      margin-top: 30px;
    }
  </style>
</head>
<body>
  <div id="heart"></div>

  <script>
    const heartDiv = document.getElementById('heart');
    const text = "rahayu";
    const width = 60;
    const height = 25;

    let frame = 0;
    let animationInterval;

    // Fungsi membuat pola hati
    function generateHeart(frameCount, useText = false) {
      let output = "";
      for (let y = 12; y > -12; y--) {
        let line = "";
        for (let x = -30; x < 30; x++) {
          let formula = Math.pow((x * 0.05), 2) + Math.pow((y * 0.1), 2) - 1;
          if (Math.pow(formula, 3) - Math.pow((x * 0.05), 2) * Math.pow((y * 0.1), 3) <= 0) {
            if (useText) {
              const char = text[(x - y + frameCount) % text.length];
              line += char;
            } else {
              line += (Math.abs((x * y + frameCount)) % 10).toString();
            }
          } else {
            line += ' ';
          }
        }
        output += line + "\n";
      }
      return output;
    }

    // Animasi angka
    function startAnimation() {
      animationInterval = setInterval(() => {
        heartDiv.textContent = generateHeart(frame);
        frame++;
        if (frame > 20) {
          clearInterval(animationInterval);
          showRahayu();
        }
      }, 100);
    }

    // Setelah animasi selesai, tampilkan "rahayu"
    function showRahayu() {
      heartDiv.textContent = generateHeart(frame, true);
    }

    // Jalankan animasi saat halaman dimuat
    window.onload = startAnimation;
  </script>
</body>
</html>
