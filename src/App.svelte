<script>
  let displayValue = '0';
  let operand1 = null;
  let operator = null;

  function handleNumberClick(event) {
    const value = event.target.textContent;
    displayValue = displayValue === '0' ? value : displayValue + value;
  }

  function handleOperatorClick(event) {
    const value = event.target.textContent;
    if (operator === null) {
      operand1 = parseFloat(displayValue);
      operator = value;
      displayValue = '0';
    } else {
      const operand2 = parseFloat(displayValue);
      const result = calculate(operand1, operand2, operator);
      operand1 = result;
      operator = value;
      displayValue = '0';
    }
  }

  function calculate(operand1, operand2, operator) {
    switch (operator) {
      case '+':
        return operand1 + operand2;
      case '-':
        return operand1 - operand2;
      case '*':
        return operand1 * operand2;
      case '/':
        return operand1 / operand2;
    }
  }

  function handleEqualsClick() {
    if (operator !== null) {
      const operand2 = parseFloat(displayValue);
      const result = calculate(operand1, operand2, operator);
      operand1 = null;
      operator = null;
      displayValue = result.toString();
    }
  }

  function handleClearClick() {
    displayValue = '0';
    operand1 = null;
    operator = null;
  }
</script>




<main>
<div class="calculator">
  <div class="display">{displayValue}</div>
  <div class="button-row">
    <button on:click={handleClearClick}>C</button>
    <button on:click={handleOperatorClick}>/</button>
  </div>
  <div class="button-row">
    <button on:click={handleNumberClick}>7</button>
    <button on:click={handleNumberClick}>8</button>
    <button on:click={handleNumberClick}>9</button>
    <button on:click={handleOperatorClick}>*</button>
  </div>
  <div class="button-row">
    <button on:click={handleNumberClick}>4</button>
    <button on:click={handleNumberClick}>5</button>
    <button on:click={handleNumberClick}>6</button>
    <button on:click={handleOperatorClick}>-</button>
  </div>
  <div class="button-row">
    <button on:click={handleNumberClick}>1</button>
    <button on:click={handleNumberClick}>2</button>
    <button on:click={handleNumberClick}>3</button>
    <button on:click={handleOperatorClick}>+</button>
  </div>
  <div class="button-row">
    <button on:click={handleNumberClick}>0</button>
    <button on:click={handleNumberClick}>.</button>
    <button on:click={handleEqualsClick}>=</button>
  </div>
</div>

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>