# Calculator
Using HTML,CSS AND JAVASCRIPT.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Scientific Calculator</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Courier New', Courier, monospace;
    }
    body {
      width: 100%;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(#c514c5,#0ce1e4);
    }
    .calculator {
      padding: 20px;
      border-radius: 16px;
      background: transparent;
      box-shadow: 0px 3px 15px rgba(165, 214, 16, 0.5);
    }
    input {
      width: 100%;
      border: none;
      padding: 24px;
      margin: 10px 0;
      background: transparent;
      box-shadow: 0px 3px 15px rgba(84, 84, 84, 0.1);
      font-size: 32px;
      text-align: right;
      color: #fff;
    }
    input::placeholder {
      color: #fff;
    }
    .button-grid {
      display: grid;
      grid-template-columns: repeat(5, 60px);
      gap: 10px;
      justify-content: center;
    }
    button {
      border: none;
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background: transparent;
      color: #fff;
      font-size: 18px;
      box-shadow: -4px -4px 10px rgba(255,255,255,0.1);
      cursor: pointer;
    }
    .eqalBtn {
      background-color: #fb148b;
    }
    .operator {
      color: #21f811;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" placeholder="0" id="inputBox" readonly />
    <div class="button-grid">
      <button class="operator">AC</button>
      <button class="operator">DEL</button>
      <button class="operator">%</button>
      <button class="operator">/</button>
      <button class="operator">sqrt</button>
      
      <button>7</button>
      <button>8</button>
      <button>9</button>
      <button class="operator">*</button>
      <button class="operator">^</button>

      <button>4</button>
      <button>5</button>
      <button>6</button>
      <button class="operator">-</button>
      <button class="operator">log</button>

      <button>1</button>
      <button>2</button>
      <button>3</button>
      <button class="operator">+</button>
      <button class="operator">ln</button>

      <button>0</button>
      <button>00</button>
      <button>.</button>
      <button class="eqalBtn">=</button>
      <button class="operator">π</button>

      <button class="operator">sin</button>
      <button class="operator">cos</button>
      <button class="operator">tan</button>
      <button class="operator">(</button>
      <button class="operator">)</button>
    </div>
  </div>

  <script>
    const input = document.getElementById('inputBox');
    const buttons = document.querySelectorAll('button');
    let expression = '';

    const replaceFunctions = (expr) => {
      return expr
        .replace(/π/g, 'Math.PI')
        .replace(/sqrt/g, 'Math.sqrt')
        .replace(/log/g, 'Math.log10')
        .replace(/ln/g, 'Math.log')
        .replace(/sin/g, 'Math.sin')
        .replace(/cos/g, 'Math.cos')
        .replace(/tan/g, 'Math.tan')
        .replace(/\^/g, '**');
    };

    buttons.forEach(button => {
      button.addEventListener('click', (e) => {
        const value = e.target.innerText;

        if (value === '=') {
          try {
            const finalExpression = replaceFunctions(expression);
            expression = eval(finalExpression).toString();
          } catch {
            expression = 'Error';
          }
        } else if (value === 'AC') {
          expression = '';
        } else if (value === 'DEL') {
          expression = expression.slice(0, -1);
        } else {
          expression += value;
        }

        input.value = expression;
      });
    });
  </script>
</body>
</html>

