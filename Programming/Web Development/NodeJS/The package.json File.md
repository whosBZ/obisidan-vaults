- Holds all the metadata about a project
- located at the root of the project
- Describes things such as name, versioning, licenses and dependencies 

```json
{
    "name": "sample-express",
    "version": "1.0.0",
    "description": "sample express server",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "run": "node index.js"
    },
    "author": "",
    "license": "ISC",
    "dependencies": {
        "express":"^4.18.2"
    },
    "devDependencies":{
	    "@types/node"
    }
}
```

## Required Fields
- Name = Name of application
- Version = The [[Semantic Versioning]] of the application

## Dependencies
- A list of all the dependencies/packages the project requires to run
- Each listed package also uses [[Semantic Versioning]].
- By default, only the major version is truly required while the minor and patch are flexible.
- Exact versions are stored in the [[The package.lock file |package.lock]] file
- When installing a project on a new machine, all dependencies in this *package.json* file will be installed into the *node_modules* folder

## Development Dependencies
- A list of all the dependencies/packages needed to do development on a project
- This list is ignored when a project is fully deployed as it is not needed to run the application
- Follows same [[Semantic Versioning]] principles