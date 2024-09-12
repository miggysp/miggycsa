---
layout: post
title: Calculator
courses: {'csa': {'week': 2}}
type: ccc
comments: True

---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        #calculator {
            display: inline-block;
            padding: 20px;
            background-color: #f1f1f1;
            border-radius: 10px;
        }
        #display {
            width: 100%;
            height: 50px;
            font-size: 24px;
            text-align: right;
            margin-bottom: 10px;
            padding: 5px;
            border-radius: 5px;
        }
        button {
            width: 70px;
            height: 70px;
            font-size: 24px;
            margin: 5px;
            cursor: pointer;
            border-radius: 5px;
            border: none;
            background-color: #4CAF50;
            color: white;
            transition: background-color 0.2s;
        }
        button:hover {
            background-color: #45a049;
        }
        .history {
            margin-top: 30px;
            width: 300px;
            background-color: #f1f1f1;
            padding: 10px;
            border-radius: 10px;
            display: inline-block;
            text-align: left;
            overflow-y: auto;
            max-height: 200px;
        }
    </style>
</head>
<body>

    <h1>Simple Calculator</h1>
    <div id="calculator">
        <input type="text" id="display" disabled />

        <div>
            <button onclick="appendNumber('7')">7</button>
            <button onclick="appendNumber('8')">8</button>
            <button onclick="appendNumber('9')">9</button>
            <button onclick="setOperation('÷')">÷</button>
        </div>
        <div>
            <button onclick="appendNumber('4')">4</button>
            <button onclick="appendNumber('5')">5</button>
            <button onclick="appendNumber('6')">6</button>
            <button onclick="setOperation('×')">×</button>
        </div>
        <div>
            <button onclick="appendNumber('1')">1</button>
            <button onclick="appendNumber('2')">2</button>
            <button onclick="appendNumber('3')">3</button>
            <button onclick="setOperation('-')">-</button>
        </div>
        <div>
            <button onclick="appendNumber('0')">0</button>
            <button onclick="setOperation('^')">^</button>
            <button onclick="calculate()">=</button>
            <button onclick="setOperation('+')">+</button>
        </div>
        <div>
            <button onclick="clearDisplay()">C</button>
            <button onclick="setOperation('%')">%</button>
            <button onclick="setOperation('√')">√</button>
            <button onclick="backspace()">⌫</button>
        </div>
    </div>

    <div class="history">
        <h2>History</h2>
        <ul id="history"></ul>
    </div>

    <script>
        let currentInput = '';
        let operation = '';
        let firstValue = null;
        let secondValue = null;
        let history = [];

        const display = document.getElementById('display');
        const historyElement = document.getElementById('history');

        function appendNumber(number) {
            currentInput += number;
            display.value = currentInput;
        }

        function setOperation(op) {
            if (currentInput === '') return;
            if (firstValue === null) {
                firstValue = parseFloat(currentInput);
                operation = op;
                currentInput = '';
            } else {
                secondValue = parseFloat(currentInput);
                calculate();
                operation = op;
                firstValue = parseFloat(display.value);
                currentInput = '';
            }
        }

        function calculate() {
            if (firstValue === null || (operation !== '√' && currentInput === '')) return;

            secondValue = operation !== '√' ? parseFloat(currentInput) : null;

            let result;
            switch (operation) {
                case '+':
                    result = firstValue + secondValue;
                    break;
                case '-':
                    result = firstValue - secondValue;
                    break;
                case '×':
                    result = firstValue * secondValue;
                    break;
                case '÷':
                    result = secondValue !== 0 ? firstValue / secondValue : 'Error';
                    break;
                case '^':
                    result = Math.pow(firstValue, secondValue);
                    break;
                case '%':
                    result = firstValue % secondValue;
                    break;
                case '√':
                    result = Math.sqrt(firstValue);
                    break;
                default:
                    return;
            }

            addToHistory();
            firstValue = result;
            currentInput = result.toString();
            display.value = currentInput;
        }

        function addToHistory() {
            let historyEntry;
            if (operation === '√') {
                historyEntry = `√${firstValue} = ${currentInput}`;
            } else {
                historyEntry = `${firstValue} ${operation} ${currentInput} = ${display.value}`;
            }
            history.push(historyEntry);
            updateHistoryDisplay();
        }

        function updateHistoryDisplay() {
            historyElement.innerHTML = '';
            history.forEach(entry => {
                const li = document.createElement('li');
                li.textContent = entry;
                historyElement.appendChild(li);
            });
        }

        function clearDisplay() {
            currentInput = '';
            firstValue = null;
            secondValue = null;
            operation = '';
            display.value = '';
        }

        function backspace() {
            currentInput = currentInput.slice(0, -1);
            display.value = currentInput;
        }
    </script>

</body>
</html>
