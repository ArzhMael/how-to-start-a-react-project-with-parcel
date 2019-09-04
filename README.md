# How To Start a React Project with Parcel ? (with ESLint and Prettier)
  
Hello ! Here is a quick step-by-step tutorial to get started on a new React project using Parcel.

***Note :** Unless otherwise specified, all commands are run from the root of the working directory*.
### Step 0 - Install NodeJS and Parcel :
- Install [**NodeJS**](https://nodejs.org/en/)
- Run ```sudo npm install -g parcel-bundler``` to install [**Parcel**](https://parceljs.org/).
### Step 1 - Initialize the project :
- Create new working directory.
- Run ```npm init -y``` to create the *package.json* file.
### Step 2 - Install Prettier and ESLint :
- Run ```npm install --save-dev --save-exact prettier``` to install [**Prettier**](https://prettier.io/) and dependencies.
- Run ```npm install eslint --save-dev``` to install [**ESLint**](https://eslint.org/) and dependencies.
- Run ```npx @becode/eslint-config --with-hook``` if you want to configure **ESLint** with [BeCode](https://www.becode.org/) formation configuration.
- If working with [**Git**](https://github.com/), run ```echo "/node_modules" >> .gitignore``` to initialise a new *.gitignore* file and add new exception for the */node_modules* folder.
- Also add exception for the */dist* folder, run ```echo "/dist" >> .gitignore```
### Step 3 - Create the project architecture :
- Run ```touch index.html``` to create the html file wich will be the entry point of the App.
- Run ```mkdir src && touch src/index.js``` to create *index.js* file inside the *src* folder.
- Add the following lines as in your *index.html* file.
```html
<!DOCTYPE html>
<html>
    <body>
        <script src="./src/index.js"></script>
    </body>
</html>
```
- Run ```mkdir components``` to create the folder wich will contains our **React** *components*.
### Step 4 - Install React :
- Run ```npm i react``` to install [React](https://reactjs.org/) and dependencies.
- Run ```npm i react-dom``` to install ReactDOM and dependencies.
- Run ```npm i babel-preset-env babel-preset-react --save-dev``` to use **Babel** to translate ES6 code to browsers' understandable code.
- Run ```touch .babelrc``` to create a config file for **Babel** and add the following lines to the file.
```
{
    "presets" : ["env" , "react"]
}

```
### Step 5 - Install Sass :
- Run ```npm i node-sass``` to install [**Sass**](https://sass-lang.com/).
- Run ```mkdir scss && touch scss/app.scss``` to create the stylesheet.
- Add the following line to *src/index.js*
```
import "../scss/app.scss";
```
### Step 6 - Configure package.json :
- Add the following lines in the *package.json* file.
```
"scripts": {
    "start": "parcel index.html",
    "build": "parcel build index.html"
},
```
# Here we are !
Your app is ready to go, just run ```npm start``` !
It's currently empty but you can add any **HTML** (in index.html), **CSS** (in scss/app.scss) or create **React Components** (in components) as you wish !   
  
If you want to have a quick look, checking if everything works, just copy thoses lines and create this *HelloMessage React component*.

###### index.html
```html
<!DOCTYPE html>
<html>
    <head>
    </head>
    <body>
        <div id="app"></div>
        <script src="./src/index.js"></script>
    </body>
</html>

```
###### src/index.js
```javascript
import React from "react";
import ReactDOM from "react-dom";

import HelloMessage from "../components/hello-message";

const App = document.querySelector("#app");
ReactDOM.render(<HelloMessage name={"Yomi"} />, App);
```
###### scss/app.scss
```scss
body {
    background-color: rgb(15, 214, 228);
    display: flex;
    justify-content: center;
    
    h1{
      font-size: 5em;
      color: white;
    }
}
```
###### components/hello-message.js
```javascript
import React from "react";

class HelloMessage extends React.Component {
    render() {
        return (
            <div>
                <div className={"container"}>
                    <h1>
                        {"Hello "} {this.props.name}
                    </h1>
                </div>
            </div>
        );
    }
}

export default HelloMessage;
```
