# Module Setup
**1. initialize modules in terminal with:**
```
npm init -y
```
- Creates a package.json
  - Can add a description
  - Change “main” from “index.js” to “src/javascripts/main.js”
  - Change scripts to:
	```
	"start": "webpack-dev-server --mode development --open",
	"build": "webpack --mode production --module-bind js=babel-loader",
	"deploy": "npm run build && firebase deploy"
	```
  - Put name in author
  - Change licence to MIT

 **2. install all regular dependencies (until React) in terminal with:**
```
npm install @babel/core @babel/preset-env babel-loader css-loader eslint eslint-config-airbnb-base eslint-loader eslint-plugin-import file-loader html-loader html-webpack-plugin mini-css-extract-plugin node-sass sass-loader webpack webpack-cli webpack-dev-server --save-dev
```

**3. paste into .gitignore:**
```
package-lock.json
node_modules/
dist/
build/
```

**4. create a file called .babelrc and paste:**
```
{
  "presets": [
      "@babel/preset-env"
  ]
}
```

**5. create a file called webpack.config.js and paste:**
```
const HtmlWebPackPlugin = require("html-webpack-plugin");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
module.exports = {
  entry: './src/javascripts/main.js',
  module: {
    rules: [
      {
        enforce: "pre",
        test: /\.js$/,
        exclude: /node_modules/,
        loader: "eslint-loader"
      },
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader",
            options: { minimize: true }
          }
        ]
      },
      {
        test: /\.scss$/,
        use: [
          MiniCssExtractPlugin.loader,
            { loader: 'css-loader', options: { sourceMap: true, importLoaders: 1 } },
            { loader: 'sass-loader', options: { sourceMap: true } },
        ],
      },
      {
        test: /\.(png|svg|jpg|gif)$/,
        use: ['file-loader']
      },
      {
        test: /\.(woff|woff2|eot|ttf|otf)$/,
        use: ['file-loader']
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./src/index.html",
      filename: "./index.html"
    }),
    new MiniCssExtractPlugin({
      filename: "[name].css",
      chunkFilename: "[id].css"
    })
  ],
  output: {
		path: __dirname + "/build",
		filename: "bundle.js"
	},
  devtool: "eval-source-map"
};
```

**6. create a file called .eslintignore and paste:**
```
webpack.config.js
node_modules/
```

**7. create a file called .eslintrc and paste:**
```
{
  "parserOptions": {
    "ecmaVersion": 6,
    "sourceType": "module"
  },
  "extends": "airbnb-base",
  "globals": {
    "document": true,
    "window": true,
    "$": true,
    "XMLHttpRequest": true,
    "allowTemplateLiterals": true
  },
  "rules": {
    "no-console": [2, { "allow": ["error"] }],
    "no-debugger": 1,
    "class-methods-use-this": 0,
    "linebreak-style": 0
  }
}
```

**8. install regular dependencies with:**
```
npm install axios bootstrap jquery popper.js --save
```

**9. create the following file structure:**
- src/
  - assets/
  - index.html
  - javascripts/
    - components/
    - helpers/
      - util.js
    - main.js
  - styles/
    - main.scss

**10. in main.scss, include:**
```
@import "~bootstrap/scss/bootstrap";

body {
  background-color: lightblue;
}

// get more at loading.io
.light-shade {
  background-color: #ffffff;
}

.light-accent {
  background-color: #bdf8bd;
}

.main-brand-color {
  background-color: #542190;
}

.dark-accent {
  background-color: #c29ecc;
}

.dark-shade {
  background-color: #5c3545;
}
```

**11. in main.js, include:**
```
import '../styles/main.scss';
import 'bootstrap';
```

**12. in util.js, include:**
```
const printToDom = (divId, textToPrint) => {
  const selectedDiv = document.getElementById(divId);
  selectedDiv.innerHTML = textToPrint;
};

export default { printToDom };
``` 

**13. init firebase **
```
firebase init
```

**13. test with:**
```
npm start
```
