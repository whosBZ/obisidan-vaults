- A typescript file without top-level imports or exports is not a module and runs in the global scope
- This results in its declarations being accessible in other modules.
- If you do however have top level imports or exports then all declarations are limited to the module scope and that module only

## Defining Custom Types

- You can define a custom type by using the type keyword.
- Custom types help simplify code and prevent inline repetition of type definitions.

```typescript
type WeatherDetailType = {
	weather: string;
	zipcode; string;
	temp?: number;
};

let weatherDetail: WeatherDetailType = {
	weather: "sunny",
	zipcode: "00000",
	temp: 30
}

const getWeatherDetails = (data: WeatherDetailType): WeatherDetailType => data;
```

- As you can see, you can create a single type definition and then reuse it everywhere

## Defining Interfaces

- An additional way of creating custom types with the difference between Type and Interface being very mild.
- You can pick whichever one you like to use but keep it consistent
- Type should be seen as an Alias for another type of union of types

```typescript
type ID = string | number // Gives a label to a union
type name = string // Gives an alias to a type 
```

- Interfaces should be seen as a description of an object
- They are defined in a similar way to types, but without an assignment sign

```typescript
interface WeatherProps { // No equal sign
	weather: string;
	zipcode: string;
	temp?: number
}
```

## Extending types and interfaces

- Both types and interfaces can be extended in different ways
- interfaces are extended by creating a new interface as an extension of an existing one
- types are extended by creating a union between an existing type and a new type or other existing type

```typescript
interface Animal {
	name: string
}

interface Bear extends Animal { 
	honey: boolean
} // Creates a new interface Bear with all Animal properties plus honey
```

```typescript
type Animal = {
	name: string
}

type Bear = Animal & {
	honey: boolean
} // Creates a union between Animal and a newly defined type

```

- Interfaces can also have new fields added to them while types cannot

```typescript
interface Window {
	title: string;
}

interface Window {
	ts: TypescriptAPI
} // This adds the field ts to the Window interface
```

```typescript
type Window = {
	title: string
}

type Window = {
	ts: TypescriptAPI
} // This just throws a duplicate identifier error
```

## Type Deceleration Files

- To use custom type universally, you can define them in *type deceleration files*, which have the *.d.ts* extension.
- These files should never contain any implementation code
- TSC uses these type definitions to understand custom types and do type checks.
- They are never transpiled to JavaScript and never part of executed script.
- Deceleration files help work with third-party libraries that aren't written in TypeScript and don't have type deceleration files in their code bases.
- These type deceleration files are handled separately
	- Can be often found in the DefinitelyTyped repository on GitHub.
	- Deceleration files for third parties can be found in [[NPM Package Manager|NPM]] under the @types scope
	- All deceleration files should be considered [[The package.json File#Development Dependencies|development dependencies]]
- By creating type files using the .d.ts extension you will have all those types available in your project without needing to import them explicitly
	- However if you add any import or export statements to your .d.ts file it will prevent this from happening as your types file is now considered a module