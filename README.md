<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>Saadet'in Rahatlama Seansı</title>
<style>
  body, html {
    margin: 0;
    padding: 0;
    height: 100%;
    overflow: hidden;
    font-family: 'Comic Sans MS', cursive, sans-serif;
    background-color: #000;
  }
  #game-container {
    position: relative;
    width: 100%;
    height: 100%;
    background: url('317DA462-E443-4B38-AB6A-19105FF675FC.jpeg') no-repeat center center;
    background-size: cover;
  }
  #logo {
    position: absolute;
    top: 10px;
    width: 100%;
    text-align: center;
    font-size: 32px;
    color: #ff3333;
    font-weight: bold;
    text-shadow: 2px 2px 5px rgba(0,0,0,0.5);
  }
  #controls {
    position: absolute;
    bottom: 20px;
    width: 100%;
    text-align: center;
  }
  .game-button {
    font-size: 20px;
    padding: 10px 20px;
    margin: 0 20px;
    border: none;
    border-radius: 10px;
    background-color: #ffcc00;
    cursor: pointer;
    box-shadow: 2px 2px 5px rgba(0,0,0,0.5);
  }
  .game-button:active {
    transform: scale(0.95);
  }
  .damage {
    position: absolute;
    width: 100px;
    opacity: 1;
    transition: opacity 0.5s ease-out;
  }
</style>
</head>
<body>
<div id="game-container">
  <div id="logo">Saadet'in Rahatlama Seansı</div>
  <div id="controls">
    <button id="punch-btn" class="game-button">Yumruk At</button>
    <button id="slap-btn" class="game-button">Tokat At</button>
  </div>
</div>

<audio id="punch-sound" src="punch.wav"></audio>
<audio id="slap-sound" src="slap.wav"></audio>

<script>
  // Buton ve ses elementlerine referanslar
  const punchBtn = document.getElementById('punch-btn');
  const slapBtn = document.getElementById('slap-btn');
  const punchSound = document.getElementById('punch-sound');
  const slapSound = document.getElementById('slap-sound');
  const gameContainer = document.getElementById('game-container');

  function showDamageEffect() {
    // Morluk görselini oluştur
    const damageImg = document.createElement('img');
    damageImg.src = 'bruise.png';
    damageImg.className = 'damage';

    // Rastgele bir konum belirle (örneğin, yüz bölgesine yakın)
    const x = Math.random() * (gameContainer.clientWidth - 100);
    const y = Math.random() * (gameContainer.clientHeight - 100);
    damageImg.style.left = x + 'px';
    damageImg.style.top = y + 'px';

    // Görseli ekle
    gameContainer.appendChild(damageImg);

    // Kısa süre sonra morluk efektini kaybolacak şekilde ayarla
    setTimeout(() => {
      damageImg.style.opacity = 0;
    }, 100);

    // Animasyon tamamlandığında elementi kaldır
    setTimeout(() => {
      gameContainer.removeChild(damageImg);
    }, 600);
