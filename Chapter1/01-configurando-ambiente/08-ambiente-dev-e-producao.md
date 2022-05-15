# Ambiente Dev e Produção

    Para que o Webpack funcione de formas diferentes, no momento de desenvolvimento e/ou quando for gerado para produção.

1. Adicionar no arquivo "webpack.config.js":

    ```js
        const path = require('path')
        const HtmlWebpackPlugin = require('html-webpack-plugin')

        const isDevelopment = process.env.NODE_ENV !== 'production';    // add

        module.exports = {
            mode: isDevelopment ? 'development' : 'production', // alterado
            devtool: isDevelopment ? 'eval-source-map' : 'source-map',  // alterado
            entry: path.resolve(__dirname, 'src', 'index.jsx'),
            output: {
                path: path.resolve(__dirname, 'dist'),
                filename: 'bundle.js'
            },
            resolve: {
                extensions: ['.js', '.jsx'],
            },
            devServer: {
                static: path.resolve(__dirname, 'public'),
            },
            plugins: [
                new HtmlWebpackPlugin({
                    template: path.resolve(__dirname, 'public', 'index.html')
                })
            ],
            module: {
                rules: [
                    {
                        test: /\.jsx$/,
                        exclude: /node_modules/,
                        use: 'babel-loader',
                    }
                ],
            }
        };
    ```

2. Criar variável de ambiente - NODE_ENV:

    Mac e Linux:
    `NODE_ENV=production yarn webpack`

    Windows e todos (Mac e Linux): independente do sistema operacional.
    `yarn add cross-env -D`

3. Criar no arquivo "package.json", os scripts:

    ```js
        {
            "name": "01-github-explorer",
            "version": "1.0.0",
            "main": "index.js",
            "license": "MIT",
            "scripts": {    // add
                "dev": "webpack serve",
                "build": "cross-env NODE_ENV=production webpack"
            },
            ...
        }
    ```

4. `yarn dev` para ambiente de desenvolvimento.

5. `yarn build` para ambiente de produção.

