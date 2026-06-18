- Typescript enables you to declare any of JavaScript's primitive types explicity
- Typescript also adds its own types such as *unions*, *tuples*, *any*, and *void*

## Primitive JavaScript Types

- *string*, *number*, *Boolean*, *undefined* and *null* are all JavaScript Primitives
- All other types are considered objects in JavaScript.
- You declare these types as below:

```typescript
let stringType: string = "bar";
let booleanType: boolean = true;
let integerType: number = 1;
let floatType: number = 1.5; // No difference between integers and floats in JS
let nullType: null = null; // Intentional absense of a value
let undefinedType: undefined = undefined; // Unintensional absense of a value
```

## union Type

- Variables or parameters that can have more than one data type

```typescript
let stringOrNumberUnionType: string | number;
stringOrNumberUnionType = "bar" // Valid
stringOrNumberUnionType = 1 // Valid
stringOrNumberUnionType = true; // Invalid and throws an error
```

- While useful, *union* types should be used sparingly and avoid if possible.
- The problem when using them is that you will need to perform manual type checks still, although you have limited it down to specific types

## array Type

^acb298

- A generic array type offering array functions similar to a JavaScript array.
- All arrays must be given the type of data they contain or you will get an error when trying to push values into it.
- Arrays can contain only a single type

```typescript
let genericArray: [] = [];
genericArray.push(1); // Will throw Argument of type 'number' is not assignable to parameter of type 'never'

let numberArray: number[] = [];
numberArray.push(2); // Works just fine
```

## object Type

- The same as a JavaScript object but allows for defining of a properties type for TSC type-check.

```typescript
let weatherDetail: {
	weather: string,
	zipcode: string,
	temp: number
} = {weather: "sunny", zipcode: "00000", temp: 1};

weatherDetail.weather = 2 // Throws an error because weather is a string
```

- While you can do inline typing like this for objects, its best to create custom types in a separate location to allow for re-usability.

## tuple Type

- A new type added by TypeScript
- Similar to an [[#^acb298|array]] but has a specified number of typed items that can be of any type
- These are similar to tuples found in Python and C#

```typescript
let validTuple: [string, number] = ["bar", 1];
let invalidTuple: [string, number] = [1, "bar"]
```

## any Type

- A generic type that can take any value
- Should be avoided at all costs
- Below shows how dangerous it can be as it pretty much removes the guardrails of static typing.

```typescript
let indifferent: any = true; // Started a boolean
indifferent = 1; // Changes to a number
indifferent = []; // Then changes to an untyped array
```

- Typescript has become stricter to by default prevent inferring any value as any and will throw an error.
- Using any on a variable also bypasses contracts specified in a function declarations parameters as you can just pass an any into any other parameter.

```typescript
const calculate = (a: any, b: any): any => a + b;
console.log(calculate(1,1)) // Valid and outputs a number
console.log(calculate(1,"1")) // Valid and outputs a string

let x: any = 1
let y: any = 2
const concat = (a: string, b: string) => a + b 
console.log(concat(x, y)) // Works just fine
```

## void Type

- Considered the opposite of *any*
- It indicates no type at all and its only use case is to annotate the return value of a function that shouldn't have one.
- So it ensures you dont return a value on a function you originally said not to return a value
```typescript
function log(msg: string): void {
	console.log(msg)
}
```