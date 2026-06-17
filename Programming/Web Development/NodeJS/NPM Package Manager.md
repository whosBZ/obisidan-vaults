- Used to manage the installation of packages from the NPM repository
- NPM Repository is a large collection of user made libraries that can be imported into your project for ease of use
- The repostiory is community run and audited, so don't trust all packages you install as its up to the community to ensure there is no malware

## Useful Commands
- **npm install** - Used to install all packages found in a location with a [[The package.json File|package.json]] file
- **npm install \<package\>** - Used to install packages as a [[The package.json File#Dependencies |Project Dependancy]]
- **npm install --save-dev \<package\>** - Used to install packages as a [[The package.json File#Development Dependencies |Development Dependency]]
- **npm audit** - Used to show all packages with possible vulnerabilities and how to fix them
- **npm prude** - Used to remove any unused packages from the *node/modules* folder

## NPX

- A tool installed with the NPM package manager.
- Allows execution of any package from the registry without installing it into your project first.
- Helps when using one off tools like for scaffolding a project or linting of a document.
- It will first check if the executable for the package is in your $PATH environment, otherwise it will install it into a central cache and not into your *node_modules* folder