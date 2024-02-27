<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Uçak Oyunu</title>
<style>
  body, html {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: skyblue;
  }
  canvas {
    image-rendering: pixelated;
  }
  .menu {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    display: none;
  }
</style>
</head>
<body>
<canvas id="gameCanvas"></canvas>
<div class="menu">
  <h1>Oyun Bitti!</h1>
  <button id="restartButton">Tekrar Oyna</button>
  <div>
    <label for="difficultyRange">Zorluk Seviyesi: </label>
    <input type="range" id="difficultyRange" min="1" max="5" value="3">
    <span id="difficultyValue">3</span>
  </div>
  <div>
    <label for="cloudDensityRange">Bulut Miktarı: </label>
    <input type="range" id="cloudDensityRange" min="1" max="5" value="3">
    <span id="cloudDensityValue">3</span>
  </div>
</div>
<div id="score" style="position: absolute; top: 10px; left: 10px; font-size: 24px; color: white;">Skor: 0</div>
<script>
  const canvas = document.getElementById("gameCanvas");
  const ctx = canvas.getContext("2d");
  const initialCanvasWidth = 800;
  const initialCanvasHeight = 600;
  const planeWidth = 40; // Uçağın genişliği
  const planeHeight = 16; // Uçağın yüksekliği
  let planeX = canvas.width / 2 - planeWidth / 2;
  let planeY = canvas.height - planeHeight - 60;
  const planeSpeed = 2;
  const cloudRadius = 20; // Bulutların boyutu
  const redCloudRadius = 30; // Kırmızı bulutun boyutu
  const redCloudProbability = 400; // Her 400 bulutta bir kırmızı bulut oluşturulacak
  const magnetForce = 4; // Mıknatıs etkisi hızı
  let clouds = [];
  let gameRunning = true;
  let score = 0;
  let difficultyLevel = 3;
  let cloudDensity = 3;
  let isMagnetActive = false; // Mıknatıs etkisinin aktif olup olmadığını belirtir

  function drawPlane() {
    ctx.fillStyle = "black";
    ctx.beginPath();
    ctx.moveTo(planeX, planeY);
    ctx.lineTo(planeX + planeWidth / 2, planeY - planeHeight);
    ctx.lineTo(planeX + planeWidth, planeY);
    ctx.closePath();
    ctx.fill();
  }

  function movePlane() {
    if (isPlaneMovingLeft && planeX > 0) {
      planeX -= planeSpeed + planeSpeed * 0.2; // Uçağın hareket hassasiyeti 2 katına çıkarıldı
    }
    if (isPlaneMovingRight && planeX < canvas.width - planeWidth) {
      planeX += planeSpeed + planeSpeed * 0.2; // Uçağın hareket hassasiyeti 2 katına çıkarıldı
    }
    if (isPlaneMovingUp && planeY > 0) {
      planeY -= planeSpeed + planeSpeed * 0.2; // Uçağın hareket hassasiyeti 2 katına çıkarıldı
    }
    if (isPlaneMovingDown && planeY < canvas.height - planeHeight) {
      planeY += planeSpeed + planeSpeed * 0.2; // Uçağın hareket hassasiyeti 2 katına çıkarıldı
    }
  }

  function clearCanvas() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
  }

  function drawCloud(x, y, isRed) {
    ctx.fillStyle = isRed ? "red" : "white";
    ctx.beginPath();
    ctx.arc(x, y, isRed ? redCloudRadius : cloudRadius, 0, Math.PI * 2);
    ctx.fill();
  }

  function moveClouds() {
    for (let i = 0; i < clouds.length; i++) {
      if (isMagnetActive && !clouds[i].isRed) {
        // Eğer mıknatıs etkisi aktifse ve bulut kırmızı değilse
        const dx = clouds[i].x - planeX;
        const dy = clouds[i].y - planeY;
        const distance = Math.sqrt(dx * dx + dy * dy);
        const forceX = magnetForce * dx / distance;
        const forceY = magnetForce * dy / distance;
        clouds[i].x += forceX;
        clouds[i].y += forceY;
      } else {
        clouds[i].y += difficultyLevel / 2;
      }
      if (clouds[i].y > canvas.height) {
        clouds[i].y = 0;
        clouds[i].x = Math.random() * canvas.width;
        if (score % redCloudProbability === 0) {
          // Her 400 bulutta bir kırmızı bulut oluştur
          createRedCloud();
        }
        score++;
        document.getElementById("score").innerText = "Skor: " + score;
      }
      if (clouds[i].x > planeX && clouds[i].x < planeX + planeWidth &&
          clouds[i].y > planeY && clouds[i].y < planeY + planeHeight) {
        if (clouds[i].isRed) {
          // Eğer kırmızı buluta dokunulduysa
          isMagnetActive = true; // Mıknatıs etkisini aktifleştir
          setTimeout(() => {
            isMagnetActive = false; // 3 saniye sonra mıknatıs pasif hale gelir
          }, 3000);
        } else {
          endGame();
          return;
        }
      }
    }
  }

  function drawClouds() {
    for (let i = 0; i < clouds.length; i++) {
      drawCloud(clouds[i].x, clouds[i].y, clouds[i].isRed);
    }
  }

  function createClouds() {
    clouds = [];
    const cloudCount = 20 * cloudDensity; // Bulut sayısı 2 katına çıkarıldı
    for (let i = 0; i < cloudCount; i++) {
      clouds.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        isRed: false
      });
    }
  }

  function createRedCloud() {
    clouds.push({
      x: Math.random() * canvas.width,
      y: 0,
      isRed: true
    });
  }

  function updateCloudDensity() {
    cloudDensity = parseInt(document.getElementById("cloudDensityRange").value);
    document.getElementById("cloudDensityValue").textContent = cloudDensity;
    createClouds();
  }

  canvas.width = initialCanvasWidth;
  canvas.height = initialCanvasHeight;

  createClouds();

  let isPlaneMovingLeft = false;
  let isPlaneMovingRight = false;
  let isPlaneMovingUp = false;
  let isPlaneMovingDown = false;

  document.addEventListener("keydown", function(event) {
    if (event.key === "ArrowLeft") {
      isPlaneMovingLeft = true;
    } else if (event.key === "ArrowRight") {
      isPlaneMovingRight = true;
    } else if (event.key === "ArrowUp") {
      isPlaneMovingUp = true;
    } else if (event.key === "ArrowDown") {
      isPlaneMovingDown = true;
    }
  });

  document.addEventListener("keyup", function(event) {
    if (event.key === "ArrowLeft") {
      isPlaneMovingLeft = false;
    } else if (event.key === "ArrowRight") {
      isPlaneMovingRight = false;
    } else if (event.key === "ArrowUp") {
      isPlaneMovingUp = false;
    } else if (event.key === "ArrowDown") {
      isPlaneMovingDown = false;
    }
  });

  document.getElementById("restartButton").addEventListener("click", restartGame);

  const difficultyRange = document.getElementById("difficultyRange");
  const difficultyValue = document.getElementById("difficultyValue");
  
  difficultyRange.addEventListener("input", function() {
    difficultyValue.textContent = this.value;
    difficultyLevel = parseInt(this.value);
  });

  const cloudDensityRange = document.getElementById("cloudDensityRange");
  cloudDensityRange.addEventListener("input", updateCloudDensity);

  function restartGame() {
    gameRunning = true;
    score = 0;
    planeX = canvas.width / 2 - planeWidth / 2;
    planeY = canvas.height - planeHeight - 60;
    document.querySelector(".menu").style.display = "none";
    updateGame();
  }

  function endGame() {
    gameRunning = false;
    document.querySelector(".menu").style.display = "block";
  }

  function updateGame() {
    clearCanvas();
    drawClouds();
    drawPlane();
    movePlane();
    moveClouds();
    if (gameRunning) {
      requestAnimationFrame(updateGame);
    }
  }

  setInterval(() => {
    isMagnetActive = false; // 3 saniye sonra mıknatıs pasif hale gelir
  }, 3000);

  updateGame();
</script>
</body>
</html>
