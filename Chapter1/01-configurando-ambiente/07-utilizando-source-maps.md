# Source Maps

    Conseguir visualizar o código original da aplicação, mesmo quando o código está embaralhado no arquivo "bundle.js".
    Vai me levar a linha exata do erro.

    Ex:

    ```js
        throw new Error('Eita, o forninho caiu!');
    ```

1. Adicionar no arquivo "webpack.config.js":

    ```js
        module.exports = {
            mode: 'development',
            devtool: 'eval-source-map', // add
            ...
        }
    ```

