# REACT SETUP:
1) `npx create-react-app react-hoarder`
    - **create-react-app** is the script
    - **intro-react** is my new app name
<br>

2) create a new repo in github with same app name
    - do NOT initialize with a README
<br>

3) `cd` into the new directory, and in CLI:
    - `$ git remote add origin git@github.com:bobbybaxter/react-hoarder.git`
    - `$ git push -u origin master`
<br>

4) `code .` then `git checkout -b setup`
<br>

5) delete App.test.js
<br>

6) create `src/styles/`
    - move `src/index.css` to this directory
    - rename `index.css` to `index.scss`
<br>

7) create `src/App/`
    - move `src/App.js`, `src/App.css`, and `src/logo.svg` to this directory
    - rename `App.css` to `App.scss`
<br>

8) in `index.js`:
    - change `import App from './App'` to `import App from './App/App'`
    - change `import 'index.css'` to `import './styles/index.scss'`
    - before `import './styles/index.scss;' add `import 'bootstrap/dist/css/bootstrap.min.css';`
<br>

9) in `App.js` 
    - change `import './App.css'` to `import './App.scss'`
    - add `<button className="btn btn-danger">help</button>` within `App()` at the bottom of the header
<br>

10) install dependencies:
    - `npm install node-sass eslint-config-airbnb-base --sav-dev`
    - `npm install axios bootstrap prop-types firebase react-router-dom reactstrap --save`
<br>

11) at root of project create `.eslintrc` and paste:
    ```
    {
    "parserOptions": {
        "ecmaVersion": 6,
        "sourceType": "module"
      },
      "extends": ["airbnb-base", "react-app"],
      "globals": {
        "document": true,
        "window": true,
        "allowTemplateLiterals": true
      },
      "rules": {
        "no-console": [1, { "allow": ["error"] }],
        "no-debugger": 1,
        "class-methods-use-this": 0,
        "linebreak-style": 0 
      }
    }
    ```
<br>

12) `npm start` to test