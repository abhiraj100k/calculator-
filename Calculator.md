<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pro Calculator</title>

<style>
    body {
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background: linear-gradient(135deg, #1e3c72, #2a5298);
        font-family: Arial, sans-serif;
    }

    .calculator {
        background: #1c1c1c;
        padding: 20px;
        border-radius: 20px;
        box-shadow: 0 15px 40px rgba(0,0,0,0.5);
        width: 320px;
    }

    .display {
        background: #000;
        color: #00ffcc;
        font-size: 28px;
        padding: 15px;
        border-radius: 10px;
        text-align: right;
        margin-bottom: 15px;
        overflow-x: auto;
    }

    .buttons {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 10px;
    }

    button {
        padding: 20px;
        font-size: 18px;
        border: none;
        border-radius: 12px;
        cursor: pointer;
        transition: 0.2s;
        background: #333;
        color: white;
        box-shadow: 0 4px #222;
    }

    button:hover {
        background: #444;
    }

    button:active {
        transform: translateY(2px);
        box-shadow: 0 2px #111;
    }

    .operator {
        background: #ff9500;
        color: white;
    }

    .operator:hover {
        background: #ffa733;
    }

    .equal {
        background: #00c853;
        color: white;
        grid-column: span 2;
    }

    .equal:hover {
        background: #00e676;
    }

    .clear {
        background: #d50000;
        color: white;
    }

    .clear:hover {
        background: #ff1744;
    }
</style>
</head>

<body>

<div class="calculator">
    <div class="display" id="display">0</div>

    <div class="buttons">
        <button class="clear" onclick="clearDisplay()">C</button>
        <button onclick="deleteLast()">DEL</button>
        <button class="operator" onclick="append('%')">%</button>
        <button class="operator" onclick="append('/')">/</button>

        <button onclick="append('7')">7</button>
        <button onclick="append('8')">8</button>
        <button onclick="append('9')">9</button>
        <button class="operator" onclick="append('*')">*</button>

        <button onclick="append('4')">4</button>
        <button onclick="append('5')">5</button>
        <button onclick="append('6')">6</button>
        <button class="operator" onclick="append('-')">-</button>

        <button onclick="append('1')">1</button>
        <button onclick="append('2')">2</button>
        <button onclick="append('3')">3</button>
        <button class="operator" onclick="append('+')">+</button>

        <button onclick="append('0')">0</button>
        <button onclick="append('.')">.</button>
        <button class="equal" onclick="calculate()">=</button>
    </div>
</div>

<script>
    let display = document.getElementById("display");

    function append(value) {
        if (display.innerText === "0") {
            display.innerText = value;
        } else {
            display.innerText += value;
        }
    }

    function clearDisplay() {
        display.innerText = "0";
    }

    function deleteLast() {
        display.innerText = display.innerText.slice(0, -1);
        if (display.innerText === "") {
            display.innerText = "0";
        }
    }

    function calculate() {
        try {
            display.innerText = eval(display.innerText);
        } catch {
            display.innerText = "Error";
        }
    }
</script>

</body>
</html>
