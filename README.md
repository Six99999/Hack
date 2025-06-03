<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>Loader | SIX</title>
  <style>
    body {
      background-color: #121212;
      color: #fff;
      font-family: Arial, sans-serif;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    .container {
      background: #1e1e1e;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 0 15px rgba(0,0,0,0.5);
      width: 300px;
      text-align: center;
    }
    input {
      width: 100%;
      padding: 10px;
      border: none;
      border-radius: 6px;
      margin-bottom: 10px;
      background: #2c2c2c;
      color: #fff;
      font-size: 16px;
    }
    button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border: none;
      border-radius: 6px;
      background: #4caf50;
      color: #fff;
      cursor: pointer;
      font-size: 16px;
      transition: background 0.3s;
    }
    button:hover {
      background: #45a049;
    }
    .notify {
      margin-top: 15px;
      padding: 10px;
      background: #333;
      border-radius: 6px;
      display: none;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>SIX Loader</h2>
    <p>Digite a Key para acessar</p>
    <input type="text" id="keyInput" placeholder="Digite a Key..." />
    <button onclick="copyKey()">Copiar Key</button>
    <button onclick="checkKey()">Check Key</button>
    <div id="notify" class="notify"></div>
  </div>

  <script>
    const correctKey = "SIX-HUB-2025";

    function copyKey() {
      navigator.clipboard.writeText(correctKey).then(() => {
        notify("Key copiada!", "success");
      });
    }

    function checkKey() {
      const userKey = document.getElementById("keyInput").value.trim();
      if (userKey === correctKey) {
        notify("Key correta! Redirecionando...", "success");
        setTimeout(() => {
          window.location.href = "https://seusite.com/hub"; // <- Troque aqui pelo seu link final
        }, 1500);
      } else {
        notify("Key incorreta! Tente novamente.", "error");
      }
    }

    function notify(message, type) {
      const notifyDiv = document.getElementById("notify");
      notifyDiv.style.display = "block";
      notifyDiv.style.background = type === "success" ? "#4caf50" : "#e53935";
      notifyDiv.textContent = message;
      setTimeout(() => {
        notifyDiv.style.display = "none";
      }, 3000);
    }
  </script>
</body>
</html>
