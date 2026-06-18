- A modern way to righting regular functions.
- Allows for more concise code
	- Both easier to right
	- Allows for one liners

```javascript
const traditionalFunction (x) {
	return x*x;
}

const arrowFunction = (x) => {
	return x*+*x;
}

const conciseArrow = x => x*x;
```

- As you can see, if the arrow function is a single statement, you can leave out the return statement

## Lexical Scope 

- Unlike regular functions, arrow functions don't bind their [[Variable Declaration#Scope|Scope]] to the object that calls the function.
- Arrow functions bind their scope to the object that defines the arrow function.
	- This means that whatever defined the arrow function at base level, meaning if the arrow function is in an object, the defining base level is the scope just outside of that object
	- When defining an object in Javascript, everything inside that object is considered to be defined by the same scope the object was defined in.
- This means that arrow functions inherit **this** from whatever defines it
- Traditional functions, do not inherit **this** from what defines it and will always look in the scope of whatever is calling the function

```javascript
this.scope = "lexical scope";

const scopeOf = { // <-- This is being defined by the global
	scope: "defining scope",
	
	traditional: function(){
		return this.scope; // <-- Means defined by global but this not inhertied
	}
	
	arrow: () => {
		return this.scope; // <-- Means defined by global but this inherited
	},
};

console.log(scopeOf.traditional()); //Prints defining scope (called by scopeOf)
console.log(scopeOf.arrow()); //Prints lexical scope (defined by global)
```