<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smart Calculator</title>
    <style>
        body {
            background-color: #f5e1e8;
            color: #ffffff;
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin-top: 100px;
        }

        #calculator {
            background-color: #64386c;
            padding: 20px;
            border-radius: 10px;
            width: 300px;
            margin: 0 auto;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        input {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: none;
            border-radius: 5px;
            font-size: 18px;
        }

        button {
            width: 48px;
            height: 48px;
            margin: 5px;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        button.operator {
            background-color: #ffb6c1;
        }

        button.equals {
            background-color: #ff69b4;
        }

        button.reset {
            background-color: #7fb3d5;
        }

        button.doubts {
            background-color: #65cc78;
            color: #ffffff;
            width: 100%; /* Make the button full width */
            height: 60px; /* Adjust height for better visibility */
        }
    </style>
</head>
<body>
    <div id="calculator">
        <input type="text" id="display" disabled>
        <br>
        <button onclick="appendToDisplay('7')">7</button>
        <button onclick="appendToDisplay('8')">8</button>
        <button onclick="appendToDisplay('9')">9</button>
        <button class="operator" onclick="appendToDisplay('/')">/</button>
        <br>
        <button onclick="appendToDisplay('4')">4</button>
        <button onclick="appendToDisplay('5')">5</button>
        <button onclick="appendToDisplay('6')">6</button>
        <button class="operator" onclick="appendToDisplay('*')">*</button>
        <br>
        <button onclick="appendToDisplay('1')">1</button>
        <button onclick="appendToDisplay('2')">2</button>
        <button onclick="appendToDisplay('3')">3</button>
        <button class="operator" onclick="appendToDisplay('-')">-</button>
        <br>
        <button onclick="appendToDisplay('0')">0</button>
        <button onclick="appendDecimal()">.</button>
        <button class="equals" onclick="calculate()">=</button>
        <button class="operator" onclick="appendToDisplay('+')">+</button>
        <br>
        <button class="reset" onclick="resetCalculator()">C</button>
        <button class="doubts" onclick="searchDoubts()">Doubts</button>
    </div>

    <script>
        function appendToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function appendDecimal() {
            const display = document.getElementById('display');
            if (!display.value.includes('.')) {
                display.value += '.';
            }
        }

        function calculate() {
            const display = document.getElementById('display');
            try {
                display.value = eval(display.value).toString();
            } catch (error) {
                display.value = 'Error';
            }
        }

        function resetCalculator() {
            document.getElementById('display').value = '';
        }

        function searchDoubts() {
            const question = prompt('Enter your question:');
            if (question) {
                const searchUrl = `https://www.google.com/search?q=${encodeURIComponent(question)}`;
                window.open(searchUrl, '_blank');
            }
        }
    </script>
</body>
</html>
