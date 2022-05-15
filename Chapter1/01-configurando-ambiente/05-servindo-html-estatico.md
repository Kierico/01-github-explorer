# Plugin para injetar o arquivo JavaScript no HTML

1. Tirar a linha de código do arquivo "index.html" da pasta "public":

    ```html
        <script src="../dist/bundle.js"></script>   <!-- remover -->

2. `yarn add html-webpack-plugin -D`

3. Adicionar no arquivo "webpack.config.js":

    ```js
        module.exports = {
            ...
            /** Add */
            plugins: [
                new HtmlWebpackPlugin({
                    template: path.resolve(__dirname, 'public', 'index.html')
                })
            ],
            ...
        };
    ```

    `yarn webpack` reeniciar o webpack.

