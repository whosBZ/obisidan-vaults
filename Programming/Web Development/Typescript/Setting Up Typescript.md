- TypeScript is not valid JavaScript, so it must be compiled into JavaScript using the tool TSC.
- TSC converts all Typescript to JavaScript by first checking all type usage and errors and then stripping all the types away and creating valid JavaScript syntax.
- TypeScript does not effect code performance other than a step needed for the compilation
- All TypeScript files use the extension *.ts* and because its a super-set of JavaScript, you can technically rename all JavaScript files to use this extension.

## Installing

- TypeScript is not a deployed language and is converted before use, therefore it can be used as a development dependency
- The below command installs all tooling needed to get started

```bash
npm install --save-dev typescript
```

## tsconfig.json

- This file is used to define your TSC configuration options.
- It is generated with the below command

```bash
npx tsc -init
```

- TSC looks for this file in the current path all all parent directories to know what rules to apply when running the compiler.
- Once generated the following are the main properties to concern yourself with

```json
{
    "extends": "@tsconfig/recommended/tsconfig.json",
    "compilerOptions": {},
    "include": [],
    "exclude": []
}
```

- **Extends** - Allows you to extend another tsconfig file in case you have a project specific configuration that might need tweaking on other services
- **compilerOptions** - Configures the transpiling step and how it should be done
- **include** - Is an array of strings that specifies patterns or filenames to transpile.
- **exclude** - Is an array of strings that specifies patterns or filenames to ignore.