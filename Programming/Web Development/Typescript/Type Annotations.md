- An optional way to explicitly tell the runtime environment which types to expect.
- You add them following the schema *variable: type*

```typescript
const calculate = (a: number, b: number) => a + b;
```

- There is a point of over-typing though and is considered an anti-pattern
- TypeScript does infer types from usage like if you are assigning a raw value to a variable, you don't need to type it.

```typescript
const myString: string = "Hello World!" // This is an antipattern
```

- There are 3 places you should think about when typing
	- Variable deceleration: Not recommended.
	- Function return value: Optional but recommended
	- Function parameters: Essential

- To declare a function return value, you do the following

```typescript
function getWeather(): string { // Type just before curly brace
	const weather = "sunny";    // Type not needed as we know its a string
	return weather
}
```