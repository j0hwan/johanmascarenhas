---
layout: page
title: calculator
permalink: /calculator/
---

Perform basic arithmetic operations:

<div style="max-width: 400px; margin: auto; text-align: center; padding: 20px; background-color: #f9f9f9; border-radius: 10px; box-shadow: 0 0 15px rgba(0,0,0,0.1);">
  <input type="text" id="result" style="width: 100%; padding: 10px; font-size: 24px; text-align: right; border: 2px solid #ddd; border-radius: 5px;" disabled>

  <div style="margin-top: 10px;">
    <button class="calc-btn" onclick="appendNumber('7')">7</button>
    <button class="calc-btn" onclick="appendNumber('8')">8</button>
    <button class="calc-btn" onclick="appendNumber('9')">9</button>
    <button class="calc-btn" onclick="setOperation('+')">+</button>
  </div>
  <div>
    <button class="calc-btn" onclick="appendNumber('4')">4</button>
    <button class="calc-btn" onclick="appendNumber('5')">5</button>
    <button class="calc-btn" onclick="appendNumber('6')">6</button>
    <button class="calc-btn" onclick="setOperation('-')">-</button>
  </div>
  <div>
    <button class="calc-btn" onclick="appendNumber('1')">1</button>
    <button class="calc-btn" onclick="appendNumber('2')">2</button>
    <button class="calc-btn" onclick="appendNumber('3')">3</button>
    <button class="calc-btn" onclick="setOperation('*')">*</button>
  </div>
  <div>
    <button class="calc-btn" onclick="appendNumber('0')">0</button>
    <button class="calc-btn" onclick="clearResult()">C</button>
    <button class="calc-btn" onclick="calculate()">=</button>
    <button class="calc-btn" onclick="setOperation('/')">/</button>
  </div>
</div>

<script>
  let currentOperation = '';
  let firstNumber = '';
  let secondNumber = '';

  function appendNumber(number) {
    const resultField = document.getElementById('result');
    if (currentOperation === '') {
      firstNumber += number;
      resultField.value = firstNumber;
    } else {
      secondNumber += number;
      resultField.value = secondNumber;
    }
  }

  function setOperation(operation) {
    if (firstNumber !== '') {
      currentOperation = operation;
    }
  }

  function calculate() {
    const resultField = document.getElementById('result');
    let result = 0;

    if (currentOperation === '+') {
      result = parseFloat(firstNumber) + parseFloat(secondNumber);
    } else if (currentOperation === '-') {
      result = parseFloat(firstNumber) - parseFloat(secondNumber);
    } else if (currentOperation === '*') {
      result = parseFloat(firstNumber) * parseFloat(secondNumber);
    } else if (currentOperation === '/') {
      result = parseFloat(firstNumber) / parseFloat(secondNumber);
    }

    resultField.value = result;
    firstNumber = result.toString();
    secondNumber = '';
    currentOperation = '';
  }

  function clearResult() {
    firstNumber = '';
    secondNumber = '';
    currentOperation = '';
    document.getElementById('result').value = '';
  }
</script>

<style>
  .calc-btn {
    width: 20%;
    padding: 15px;
    font-size: 18px;
    margin: 5px;
    background-color: #3498db;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  .calc-btn:hover {
    background-color: #2980b9;
  }

  .calc-btn:active {
    background-color: #1c6ea4;
  }
</style>


