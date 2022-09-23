# Webpack Notes

## Basic setup

    npm init -y                 // initiate a basic JSON file 'package.json'

The ```package.json``` file will save references to our installed modules. With the ```-y``` option, we can answer 'yes' to all the prompted questions, populating the package.json file as such: 

    {
        "name": "webpack_beginners",
        "version": "1.0.0",
        "description": "",
        "main": "index.js",
        "scripts": {
            "test": "echo \"Error: no test specified\" && exit 1"
        },
        "keywords": [],
        "author": "",
        "license": "ISC"
    }
    
### Install Webpack

    npm install webpack webpack-cli --save-dev

The ```--save-dev``` option tells NPM that we need this just for our development purposes. The packages will be installed on our local machine only. This command also adds the following to our package.json file:

    "devDependencies": {
        "webpack": "^5.74.0",
        "webpack-cli": "^4.10.0"
    }

We also can see the ```node_modules``` folder and the ```package-lock.json``` file installed in the directory. Remember the following:

- ```package.json``` lists all packages a project depends on; anything that gets installed is added to this file as well. 
- ```package-lock.json``` is the full representation of the dependency tree of the project. If someone later takes your project and ran ```npm  install```, they would get an exact copy of the original.

### Running Webpack

When webpack runs, it uses a point of entry - ```src/index```, and will output the result to ```dist/main/js```. It expects there to be an entry file called ```index.js``` inside a ```src```folder, while the output is expectex to go to the ```dist/main.js``` file. 

    node_modules/.bin/webpack       // tell webpack to bundlel our JS

### Simplify the Webpack Command

Replace the default input in your ```package.json``` file and add ```"build": "webpack --mode=production"``` to the 'script' section. This makes it so we can run:

    npm run build

This will look for a webpack command in the node_modules folder and call it for us. 