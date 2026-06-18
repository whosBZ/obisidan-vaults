- Variables can be declared using var, let, and const
- **var** has be labelled as outdated, but still has a place in java script
## Scope
- JavaScript multiple levels of code areas called scopes
	- global
	- module
	- function
	- block

### Block Scope
- Applies to any block of code enclosd in curly brackets
- The smallest unit of scope
- Anytime you use curly braces, that creates a scope

```javascript
{ //Start of scope
	let x = 1
	const y = 'hello'
	const z = null
} //End of scope
```

### Function Scope
- When you define a function, all code within that function is in that functions scope.
- As before, a function creates its own scope between curly braces.
- However if you create a new scope inside that function, that wrapping function does not have access to that block inside it, but that block has access to the block outside it.

```javascript
const function foo () { // Start of function scope
	let x = 1
	const y = 'foo'
	const z = null
	
	for(let i = 0, i<= 1, i++){ // Start of block scope
		const counted = i;
		console.log(y + counted); // y is accessible in block
	} // End of block scope
	
	console.log(counted) // This will throw an error as counted is out of scope
	
	return y
} // End of function scope
```

### Module Scope
- Applies to a single module .
- All code within a module applies Block Scope and Function scope to just that file.
- Only what you have exported can be made accessible from a module.

### Global Scope
- The outer most scope of a program, will be the root of the java script file.
- Imported modules do not have access to a separate files global scope.
- Likewise unless explicitly exported by default, the importing file does not have access to global variables in a modules


## Hoisting Variables
- Can cause a lot of havoc on a developer managing variable scope
### var 
- The tradition way of declaring a variable in JavaScript
```javascript
var fooVar = "1" // Global scope
function bar () {
	var barVar = "2" // Function scope
	return barVar
}
```

- However, **var** variables are considered hoisted variables, meaning that if declared in the code they are always accessible in that blocks scope even with code written before its deceleration

```javascript
console.log(fooVar) // Can acess fooVar but it is undefined
var fooVar = "1"
```

- This is due to JavaScript first running through a whole file and adding any declared variables to the scope manager. 
- When the file executes, it asks the scope manager if the variable exists in the code, it will say yes and its a hoisted variable, but it is not initialised. This makes the JavaScript engine initialise the variable at runtime without issues.
- If declared outside a function block it is a global variable and globally scoped and  can be hoisted to the global scope.
- If declared inside a function block is is function scoped and not accessible outside even if its using **var** but will still be hoisted to the top of that function/block scope.
- Regarding function blocks though, if you declare a var inside a block that is inside a function block. You can access that var outside of its nested block (This is what ruins developers) 

```javascript
console.log(fooVar) // This works 
console.log(farVar) // This works 

var fooVar = "1" // Global scope
console.log(barVar) // This does not work and is out of scope

function bar () {
	console.log(barVar) // This works
	console.log(farVar) // This also works
	console.log(nestedBar) // This also works but nestedBar is undefined
	if (true) {
	    var nestedBar = "nestedBar";
	}
	var barVar = "2" // Function scope
	console.log(nestedBar) // This also works but nestedBar has a value now
	return barVar
}

var farVar = 3
```

- This is prevented when running in strict mode as all variables must be initialised before use in strict mode.
### let

- The modern JavaScript way of declaring variables
```javascript
let fooVar = "1" // Global scope
function bar () {
	let barVar = "2" // Function scope
	return barVar
}
```

- Unlike using **var** these variables are not hoisted
- They are block scoped and can only be used after initialisation

```javascript
console.log(fooVar) // Will throw an error
let fooVar = "1"
```

### const
- Used to declare constant values.
- Acts the same was that **let** does with regards to scoping and hoisting
- It is misunderstood that **const** is immutable in JavaScript, this isn't the case
	- **const** actually just prevents the changing of references to a value.
	- For primitive data types it blocks changing of the value at that reference.
	- For non primitive data types (arrays, objects) you cannot change the data type but you can add to the object.

```javascript
const primitiveDataType = 1;
primitiveDataType = 2 // Throws an error

const nonPrimitiveDataType = []
nonPrimitiveDataType.push(1) // Works just fine
nonPrimitiveDataType = 3 // Throws an error
```