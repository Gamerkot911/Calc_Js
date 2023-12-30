# Calc_Js
function calculate(operationString) {
  const operations = ["+", "-", "*", "/"];
  let operator;
  for (let op of operations) {
    if (operationString.includes(op)) {
      operator = op;
      break;
    }
  }
  
  if (!operator) {
    throw "Invalid operator";
  }
  
  const operands = operationString.split(operator).map(num => {
    if (isNaN(parseInt(num, 10))) {
      throw "Invalid operand";
    }
    return parseInt(num, 10);
  });

  if ((operands[0] < 1 || operands[0] > 10) || (operands[1] < 1 || operands[1] > 10)) {
    throw "Operand out of range";
  }

  let result = 0;
  switch (operator) {
    case "+":
      result = operands[0] + operands[1];
      break;
    case "-":
      result = operands[0] - operands[1];
      break;
    case "*":
      result = operands[0] * operands[1];
      break;
    case "/":
      if (operands[0] % operands[1] !== 0) {
        throw "Division result is not an integer";
      }
      result = operands[0] / operands[1];
      break;
  }

  return result.toString();
}
