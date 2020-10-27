Using React with Spring Boot
  Add tool building dependency to pom.xml (code in pom.xml in this directory)
  Create package.json with, at a minimum
    {
      "dependencies": {
        "react": "^16.13.1",
        "react-dom": "^16.13.1",
        "rest": "^1.3.2",
      },
      "scripts": {
        "watch": "webpack --watch -d --output ./target/classes/static/built/bundle.js"
      },
      "devDependencies": {
        "@babel/core": "^7.11.6",
        "@babel/preset-env": "^7.11.5",
        "@babel/preset-react": "^7.10.4",
        "babel-loader": "^8.1.0",
        "webpack": "^4.44.2",
        "webpack-cli": "^3.3.12"
      }
    }

  Create webpack.config.js
    var path = require('path');

    module.exports = {
        entry: './src/main/js/app.js',
        devtool: 'sourcemaps',
        cache: true,
        mode: 'development',
        output: {
            path: __dirname,
            filename: './src/main/resources/static/built/bundle.js'
        },
        module: {
            rules: [
                {
                    test: path.join(__dirname, '.'),
                    exclude: /(node_modules)/,
                    use: [{
                        loader: 'babel-loader',
                        options: {
                            presets: ["@babel/preset-env", "@babel/preset-react"]
                        }
                    }]
                }
            ]
        }
    };

  Put css code in
    src/main/resources/static/main.css

  Put html template in
    src/main/resources/templates/index.html

  Put Java code in
    src/main/java/<package>

  Put js code in
    src/main/js
