- A simple way to add variables and expressions to strings
- Uses backticks (\`) instead of traditional quotation marks
- Allows the use of quotation marks inside them

## Untagged Template Literal

- Just a string enclosed in back ticks
- Parser will interpolate the variables and expressions and return a string

```javascript
let a = 1
let b = 2
let string = `${a} + ${b} = ${a +b }`

console.log(string) // Prints out 3
```

## Tagged template Literal

- A template literal with an attached expression preceding it.
- The attached function receives both the template literal and substitution values.
- It then performs a defined action with both of them and returns a value which can be primitive or non primitive.

```javascript
function tagFunction(literal, ...values) {
  let result;
  switch (literal[1]) {
    case " plus ":
      result = values[0] + values[1];
      break;
    case " minus ":
      result = values[0] - values[1];
      break;
    default:
      return "Not a valid question";
  }
  return `${values[0]}${literal[1]}${values[1]} is ${result}`;
}

let a = 1;
let b = 2;
let output = tagFunction`What is ${a} plus ${b}?`;

console.log(output); // Prints 1 plus 2 is 3
```