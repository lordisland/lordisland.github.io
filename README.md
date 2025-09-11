https://discord.com/api/guilds/1120333497572261888/widget.json

<iframe src="https://discord.com/widget?id=1120333497572261888&theme=dark" width="350" height="500" allowtransparency="true" frameborder="0" sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts"></iframe>


<!DOCTYPE html>
<html>
<head>
  <title>Code Redeem</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; }
    input, button { padding: 10px; margin: 5px 0; }
    .success { color: green; }
    .error { color: red; }
  </style>
</head>
<body>

  <h2>🎁 Redeem Kode Reward</h2>
  <p>Masukkan Gamertag kamu untuk mendapatkan kode reward (hanya 1x pakai!)</p>

  <input type="text" id="gamertagInput" placeholder="Masukkan Gamertag">
  <button onclick="redeemCode()">Redeem</button>

  <p id="message"></p>

  <script>
    // Simulasi database pemain dan kode
    const players = [
      { name: "Gerall6860", redeemed: false },
      { name: "Rizki234", redeemed: false },
      { name: "SalsaX", redeemed: false },
    ];

    const codes = [
      { code: "LOL123", used: false },
      { code: "WIN456", used: false },
      { code: "GOLD789", used: false },
    ];

    // Load data dari localStorage (agar kode tidak bisa ditebus dua kali)
    function loadData() {
      const savedPlayers = JSON.parse(localStorage.getItem("players"));
      const savedCodes = JSON.parse(localStorage.getItem("codes"));
      if (savedPlayers) {
        players.splice(0, players.length, ...savedPlayers);
      }
      if (savedCodes) {
        codes.splice(0, codes.length, ...savedCodes);
      }
    }

    function saveData() {
      localStorage.setItem("players", JSON.stringify(players));
      localStorage.setItem("codes", JSON.stringify(codes));
    }

    function redeemCode() {
      loadData(); // pastikan ambil data terbaru

      const inputName = document.getElementById("gamertagInput").value.trim();
      const message = document.getElementById("message");
      message.textContent = "";
      message.className = "";

      if (!inputName) {
        message.textContent = "❌ Masukkan gamertag terlebih dahulu.";
        message.className = "error";
        return;
      }

      // Cari player
      const player = players.find(p => p.name.toLowerCase() === inputName.toLowerCase());
      if (!player) {
        message.textContent = "❌ Gamertag tidak ditemukan.";
        message.className = "error";
        return;
      }

      if (player.redeemed) {
        message.textContent = "⚠️ Kamu sudah pernah menukarkan kode.";
        message.className = "error";
        return;
      }

      // Cari kode yang belum digunakan
      const availableCodes = codes.filter(c => !c.used);
      if (availableCodes.length === 0) {
        message.textContent = "❌ Semua kode sudah digunakan.";
        message.className = "error";
        return;
      }

      // Ambil satu kode acak
      const randomCode = availableCodes[Math.floor(Math.random() * availableCodes.length)];

      // Tandai sebagai digunakan
      player.redeemed = true;
      randomCode.used = true;

      saveData(); // Simpan data

      message.textContent = `✅ Selamat ${player.name}, kode reward kamu adalah: ${randomCode.code}`;
      message.className = "success";
    }

    // Inisialisasi data pertama kali jika belum ada
    if (!localStorage.getItem("players") || !localStorage.getItem("codes")) {
      saveData();
    }
  </script>
.
</body>
</html>


<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>🎁 Code Redeem Event</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(135deg, #2b5876, #4e4376);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .redeem-card {
      background: white;
      border-radius: 12px;
      padding: 30px;
      width: 100%;
      max-width: 400px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      text-align: center;
    }

    .redeem-card h2 {
      color: #333;
      margin-bottom: 10px;
    }

    .redeem-card p {
      font-size: 14px;
      color: #555;
      margin-bottom: 20px;
    }

    input[type="text"] {
      width: 100%;
      padding: 12px;
      font-size: 16px;
      border: 2px solid #ccc;
      border-radius: 8px;
      margin-bottom: 15px;
      outline: none;
      transition: border 0.3s;
    }

    input[type="text"]:focus {
      border-color: #4e4376;
    }

    button {
      width: 100%;
      background-color: #4e4376;
      color: white;
      border: none;
      padding: 12px;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    button:hover {
      background-color: #3a3058;
    }

    #message {
      margin-top: 20px;
      font-weight: bold;
    }

    .success {
      color: green;
    }

    .error {
      color: red;
    }
  </style>
</head>
<body>

  <div class="redeem-card">
    <h2>🎁 Redeem Kode Hadiah</h2>
    <p>Masukkan gamertag kamu untuk
