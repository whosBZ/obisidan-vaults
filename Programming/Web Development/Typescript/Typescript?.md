- A super-set of [[]] that adds static typing to the dynamic language.
- Existing JavaScript is still valid Typescript just without types.

## Benefits

- Makes working with the JavaScript type system less error prone
- Compiles so errors are seen instantly like trying to apply a .map on a variable that isn't an array
- JavaScript is also weakly typed, meaning it can change the type of a variable during runtime

```javascript
let string = "1"
let number = 1
let result;

result = number + number;
console.log("value: ", result, "type of ", typeof(result));// Prints type number

result = number + string;
console.log("value: ", result, "type of", typeof(result)); // Prints type string
```

- Untyped variables also make function and API contracts hard to work with
	- When a function takes a parameter it implicitly expects a parameter of a specific type but without typing there is no guarentee.
	- Same issue with return values, if we don't know what should be returned it can cause issues using that function.
	- If the function limits what is taken in it can also ensure what is returned out.

```javascript
let string = "1";
let number = 1;
let result;

const calculate = (a, b) => a + b;

result = calculate(number, number);
console.log("value: ", result, " type of ", typeof(result));// Prints type number

result = calculate(number, string);
console.log("value: ", result, " type of ", typeof(result));// Prints type string
```

- You could technically add checking to the functions themselves, but this adds noise to the code and you also need to run the code to test that it works
- TypeScript helps to show the errors as they happen in the IDE and then also when TSC is run to compile to JavaScript it is checked again.