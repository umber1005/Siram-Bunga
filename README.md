<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Sirami Bunga Matahari</title>
  <style>
    body {
      font-family: 'Comic Sans MS', cursive;
      text-align: center;
      background: linear-gradient(to top, #dfffe2, #ffffff);
      margin: 0;
      padding: 0;
    }

    h1 {
      color: #ffb300;
      margin-top: 20px;
    }

    #game-container {
      margin-top: 30px;
      position: relative;
    }

    #sunflower {
      transition: transform 0.4s ease;
      width: 120px;
      height: auto;
    }

    #watering-can {
      width: 70px;
      position: absolute;
      left: 50%;
      top: 0;
      transform: translateX(-50%);
      display: none;
      animation: pour 1s linear;
    }

    @keyframes pour {
      0% { top: 0; opacity: 0; }
      50% { top: 50px; opacity: 1; }
      100% { top: 0; opacity: 0; }
    }

    button {
      padding: 12px 25px;
      background-color: #4caf50;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 18px;
      cursor: pointer;
      margin: 10px;
    }

    button:hover {
      background-color: #388e3c;
    }

    #water-count, #message {
      margin-top: 10px;
      font-size: 18px;
    }

    #message {
      font-weight: bold;
      color: #e65100;
    }
  </style>
</head>
<body>

  <h1>🌻 Sirami Bunga Matahari 🌻</h1>

  <div id="game-container">
    <img id="watering-can" src="https://cdn-icons-png.flaticon.com/512/2909/2909761.png" alt="Penyiram">
    <img id="sunflower" src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/40/Sunflower_sky_backdrop.jpg/200px-Sunflower_sky_backdrop.jpg" alt="Bunga Matahari">
  </div>

  <button onclick="sirami()">💧 Sirami!</button>
  <button onclick="isiAir()">🌧️ Tunggu Hujan</button>

  <div id="water-count">Air tersisa: <span id="water">5</span></div>
  <div id="message"></div>

  <script>
    let scale = 1;
    let water = 5;

    const flower = document.getElementById('sunflower');
    const waterEl = document.getElementById('water');
    const message = document.getElementById('message');
    const wateringCan = document.getElementById('watering-can');

    function sirami() {
      if (water > 0) {
        water--;
        scale += 0.1;
        flower.style.transform = `scale(${scale})`;
        waterEl.textContent = water;
        message.textContent = "Bunga tumbuh! 😊";

        // Tampilkan animasi penyiraman
        wateringCan.style.display = 'block';
        setTimeout(() => wateringCan.style.display = 'none', 1000);

        if (scale > 1.6) {
          message.textContent = "Bunga sangat bahagia! 🌼";
        }
      } else {
        message.textContent = "Air habis! Klik 'Tunggu Hujan'.";
      }
    }

    function isiAir() {
      water = 5;
      waterEl.textContent = water;
      message.textContent = "Air sudah penuh kembali! 💧";
    }
  </script>

</body>
</html>
