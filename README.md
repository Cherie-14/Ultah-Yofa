<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Selamat Ulang Tahun Yofa</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to top right, #fceabb, #f8b500);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      color: #333;
      text-align: center;
    }
    h1 {
      font-size: 2.5em;
      margin-bottom: 0.2em;
    }
    h2 {
      margin-bottom: 1.5em;
    }
    #cake {
      position: relative;
      width: 200px;
      height: 200px;
      background: #d2691e;
      border-radius: 10px;
      margin-bottom: 1em;
    }
    #flame {
      position: absolute;
      top: -40px;
      left: 90px;
      width: 20px;
      height: 40px;
      background: orange;
      border-radius: 50% 50% 50% 50%;
      animation: flicker 0.3s infinite;
    }
    @keyframes flicker {
      0% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.6; transform: scale(1.1); }
      100% { opacity: 1; transform: scale(1); }
    }
    button {
      padding: 10px 20px;
      font-size: 1em;
      background-color: #ffb347;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      box-shadow: 2px 2px 6px rgba(0,0,0,0.2);
    }
    button:hover {
      background-color: #ffc966;
    }
  </style>
</head>
<body>
  <h1>Selamat Ulang Tahun ke-26</h1>
  <h2>Untuk kamu yang paling ku sayang<br>Yofa Kautsar Putra 🎉</h2>
  <div id="cake">
    <div id="flame"></div>
  </div>
  <button onclick="startListening()">Tiup lilin 🎂</button>

  <script>
    let flame = document.getElementById("flame");

    function startListening() {
      if (!('webkitSpeechRecognition' in window)) {
        alert('Browser kamu tidak mendukung speech recognition. Coba di Chrome ya!');
        return;
      }

      const recognition = new webkitSpeechRecognition();
      recognition.lang = 'id-ID';
      recognition.continuous = false;
      recognition.interimResults = false;

      recognition.start();

      recognition.onresult = function(event) {
        const hasil = event.results[0][0].transcript.toLowerCase();
        if (hasil.includes("tiup") || hasil.includes("tiup lilin") || hasil.includes("hup") || hasil.includes("fuuu")) {
          flame.style.display = "none";
          alert("Lilin sudah ditiup! 🎉");
        } else {
          alert("Coba bilang 'tiup lilin' atau 'fuuu'");
        }
      };

      recognition.onerror = function() {
        alert("Ups, coba lagi ya!");
      };
    }
  </script>
</body>
</html>
