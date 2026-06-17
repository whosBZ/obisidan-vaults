- An auto generated file whenever npm installs packages for the first time

```json
{
    "name": "sample-express",
    "lockfileVersion": 2,
    "requires": true,
    "packages": {
        "": {
            "dependencies": {
                "express": "^4.18.2"
            }
        },
        "node_modules/accepts": {
            "version": "1.3.8",
            "resolved": "https://­registry​.­npmjs​.­org​/­accepts​/­​-­​/­accepts​-­1​.­3​.­8​.­tgz",
            "integrity": "sha512-PYAthTa2m2VKxuvSD3DPC/Gy+U+sOA1LAuT8mkmRuvw+NACSaeXEhosdQ==",
            --snip--
        },
        --snip--
        "node_modules/express": {
            "version": "4.18.2",
            "resolved": "https://­registry​.­npmjs​.­org​/­express​/­​-­​/­express​-­4​.­18​.­2​.­tgz",
            "integrity": "sha512-5/PsL6iGPdfQ/lKM1UuielYgv3BUoJfz1aUwU9vHZ+J7gyvwdQXFEBIEI==",
            "dependencies": {
                "accepts": "~1.3.8",
                --snip--
                "vary": "~1.1.2"
            },
            "engines": {
                "node": ">= 0.10.0"
            }
        },
        --snip--
        "vary": {
            "version": "1.1.2",
            "resolved": "https://­registry​.­npmjs​.­org​/­vary​/­​-­​/­vary​-­1​.­1​.­2​.­tgz",
            "integrity": "sha512-BNGbWLfd0eUPabhkXUVm0j8uuvREyTh5ovRa/dyow/BqAbZJyC+bfhskkh=="
        }
    }
}
```

- Helps track exact [[Semantic Versioning]] of packages used in the project
	- Helps prevent against bad versioning quality control on npm packages
	- Ensures every project on every pc is using the exact same version
- It also stores all the packages that the main installed package depends on and its location in the *node/modules* folder