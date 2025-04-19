# calculadora-hellokitty
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Calculadora Hello Kitty</title>
  <style>
    body {
      background-color: #f8a5c2;
      font-family: 'Comic Sans MS', cursive, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .calc-container {
      background-color: #ffe6f0;
      border-radius: 25px;
      padding: 20px;
      box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
      width: 320px;
      text-align: center;
      position: relative;
    }

    .kitty-image-space {
      width: 100%;
      height: 100px;
      background-color: #fdd;
      border-radius: 15px;
      margin-bottom: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      color: #c98;
    }

    .display {
      width: 100%;
      height: 50px;
      background-color: #fff;
      border: 2px solid #f9c;
      border-radius: 12px;
      font-size: 24px;
      padding: 10px;
      text-align: right;
      box-sizing: border-box;
      margin-bottom: 15px;
      font-family: 'Courier New', Courier, monospace;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    button {
      padding: 15px;
      font-size: 18px;
      border: none;
      border-radius: 12px;
      background-color: #ffb6c1;
      box-shadow: 2px 2px 5px #ccc;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background-color: #ff99b0;
    }
  </style>
</head>
<body>
  <div class="calc-container">
    <div class="kitty-image-space">
      Espaço para imagem da Hello Kitty 🐱🎀
    </div>
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button onclick="append('7')">🎀7</button>
      <button onclick="append('8')">🎀8</button>
      <button onclick="append('9')">🎀9</button>
      <button onclick="operate('/')">🎀÷</button>

      <button onclick="append('4')">🎀4</button>
      <button onclick="append('5')">🎀5</button>
      <button onclick="append('6')">🎀6</button>
      <button onclick="operate('*')">🎀×</button>

      <button onclick="append('1')">🎀1</button>
      <button onclick="append('2')">🎀2</button>
      <button onclick="append('3')">🎀3</button>
      <button onclick="operate('-')">🎀−</button>

      <button onclick="append('0')">🎀0</button>
      <button onclick="append('.')">🎀.</button>
      <button onclick="calculate()">🎀=</button>
      <button onclick="operate('+')">🎀+</button>

      <button onclick="clearDisplay()">🧼AC</button>
      <button onclick="backspace()">⬅️</button>
      <button onclick="sqrt()">√</button>
    </div>
  </div>

  <script>
    let currentInput = '';

    function updateDisplay() {
      document.getElementById('display').textContent = currentInput || '0';
    }

    function append(char) {
      currentInput += char;
      updateDisplay();
    }

    function operate(op) {
      if (currentInput !== '') {
        currentInput += op;
        updateDisplay();
      }
    }

    function calculate() {
      try {
        currentInput = eval(currentInput).toString();
      } catch (e) {
        currentInput = 'Erro';
      }
      updateDisplay();
    }

    function clearDisplay() {
      currentInput = '';
      updateDisplay();
    }

    function backspace() {
      currentInput = currentInput.slice(0, -1);
      updateDisplay();
    }

    function sqrt() {
      try {
        currentInput = Math.sqrt(eval(currentInput)).toString();
      } catch (e) {
        currentInput = 'Erro';
      }
      updateDisplay();
    }
  </script>
</body>
</html>
