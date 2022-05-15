# Webpack Dev Server

    Automatiza (cria o bundle de novo), o webpack fica observando toda alteração da aplicação, sem precisar inicializar o webpack.

1. `yarn add webpack-dev-server -D`

2. Adicionar no arquivo "webpack.config.js":

    ```js
        module.exports = {
            ...
            devServer: {
                static: path.resolve(__dirname, 'public'),
            },
            ...
        };
    ```

3. `yarn webpack serve`

