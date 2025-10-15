<!DOCTYPE html>

<html lang="en">

<head>

  <meta charset="UTF-8">

  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Hacker Style Website</title>

  <style>

    body {

      margin: 0;

      padding: 0;

      overflow: hidden;

      background: black;

      color: #00ff00;

      font-family: monospace;

    }

    canvas {

      position: absolute;

      top: 0;

      left: 0;

      z-index: -1;

    }

    .terminal {

      position: absolute;

      top: 15%;

      left: 10%;

      font-size: 20px;

      text-shadow: 0 0 5px #00ff00, 0 0 10px #00ff00;

      width: 80%;

    }

    .cursor {

      display: inline-block;

      width: 10px;

      background: #00ff00;

      margin-left: 5px;

      animation: blink 0.7s infinite;

    }

    @keyframes blink {

      0%, 50% { opacity: 1; }

      51%, 100% { opacity: 0; }

    }

    .input-box {

      background: black;

      border: none;

      border-bottom: 2px solid #00ff00;

      color: #00ff00;

      font-size: 18px;

      padding: 5px;

      outline: none;

      width: 300px;

      margin: 10px 0;

    }

    .btn {

      background: transparent;

      border: 2px solid #00ff00;

      color: #00ff00;

      padding: 8px 20px;

      margin: 5px;

      font-size: 16px;

      cursor: pointer;

      transition: 0.3s;

      text-shadow: 0 0 5px #00ff00;

    }

    .btn:hover {

      background: #00ff00;

      color: black;

      box-shadow: 0 0 15px #00ff00;

    }

    #output {

      margin-top: 20px;

      white-space: pre-line;

    }

  </style>

</head>

<body>

  <canvas id="matrix"></canvas>

  <div class="terminal">

    <h2>HACKER LOGIN PORTAL</h2>

    <input type="text" id="username" class="input-box" placeholder="Enter Username">

    <br>

    <input type="password" id="password" class="input-box" placeholder="Enter Password">

    <br>

    <button class="btn" onclick="login()">Login</button>

    <button class="btn" onclick="reboot()">Reboot</button>

    <button class="btn" onclick="exitSystem()">Exit</button>

    <div id="output"></div>

  </div>

  <script>

    // Matrix Rain Effect

    const canvas = document.getElementById("matrix");

    const ctx = canvas.getContext("2d");

    canvas.height = window.innerHeight;

    canvas.width = window.innerWidth;

    const letters = "01ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");

    const fontSize = 16;

    const columns = canvas.width / fontSize;

    const drops = Array(Math.floor(columns)).fill(1);

    function draw() {

      ctx.fillStyle = "rgba(0, 0, 0, 0.05)";

      ctx.fillRect(0, 0, canvas.width, canvas.height);

      ctx.fillStyle = "#0F0";

      ctx.font = fontSize + "px monospace";

      for (let i = 0; i < drops.length; i++) {

        const text = letters[Math.floor(Math.random() * letters.length)];

        ctx.fillText(text, i * fontSize, drops[i] * fontSize);

        if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {

          drops[i] = 0;

        }

        drops[i]++;

      }

    }

    setInterval(draw, 33);

    // Fake Login System

    function login() {

      const user = document.getElementById("username").value;

      const pass = document.getElementById("password").value;

      const output = document.getElementById("output");

      output.innerHTML = "> Verifying credentials...\n";

      setTimeout(() => {

        if (user === "admin" && pass === "1234") {

          output.innerHTML += "> ACCESS GRANTED ✅\n";

          fakeCommands();

        } else {

          output.innerHTML += "> ACCESS DENIED ❌\n";

        }

      }, 1500);

    }

    function reboot() {

      document.getElementById("output").innerHTML = "> System rebooting...\n";

      setTimeout(() => {

        document.getElementById("output").innerHTML += "> Done.\n";

      }, 2000);

    }

    function exitSystem() {

      document.getElementById("output").innerHTML = "> Exiting system...\n";

    }

    function fakeCommands() {

      const output = document.getElementById("output");

      let commands = [

        "> Initializing backdoor...",

        "> Bypassing firewall...",

        "> Accessing server 192.168.1.1...",

        "> Downloading files...",

        "> Upload Complete!"

      ];

      let i = 0;

      let interval = setInterval(() => {

        if (i < commands.length) {

          output.innerHTML += commands[i] + "\n";

          i++;

        } else {

          clearInterval(interval);

        }

      }, 1000);

    }

  </script>

</body>

</html>
