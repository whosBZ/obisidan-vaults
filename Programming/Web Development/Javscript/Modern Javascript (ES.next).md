# Modules

- Allows the separation of code into files for improved maintenance and test-ability.
- Encapsulates logic into reusable code allowing for reuse of variable and functions names without running into conflicts due to module scope.
- Allows the use of *import* statements to bring libraries into a file instead of using unofficial formats like *require*

``` javascript
const express = require('express') // Old method
import express from 'express' // New ES.next Method
```

## Named and Default Exports

- Named exports are used to export specific functions/objects from a module
- Default exports are used when there is a single purpose for the module or the module has a default functionality if you don't need to import specifics

```javascript
// Default Export
const getFoo = function () {
	return 'foo';
};

export default getFoo

// Named exports
const getBar = function () {
	return 'bar'
}

const getBaz = function () {
	return 'baz'
}

export {getBar, getBaz}
```


## Importing Modules

- For named exports you must import using curly brackets with the exact export you want to target
- For default exports you will just use the default export name without curly brackets

```javascript
// Default Import
import getFood from "default.js";

// Named Import
import { getBar, getBaz } from "named.js";
```