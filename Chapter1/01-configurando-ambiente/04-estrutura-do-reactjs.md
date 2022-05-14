1. Crie uma `<div id="root"></div>` no "body" do arquivo "index.html" na pasta "public".

2. No arquivo "index.jsx" na pasta "src", importe:

    ```js
        import React from 'react';
        import { render } from 'react-dom';
        import { App } from './App';

        /** No "render" se recebe dois parâmetros:
         *  1° parâmetro: o quê que vai ser renderizado;
         *  2° parâmetro: dentro que qual elemento será rederizado.
         */
        render(<h1>Test</h1>, document.getElementById('root'));
    ```

    `yarn webpack` exculta o webpack.

3. No arquivo "index.html" na pasta "public", adicione:

    ```html
        <!-- abaixo da div com id root. -->
        <script src="../dist/bundle.js"></script>   <!-- add -->
    ```

4. Passar uma configuração no arquivo "babel.config.js" para não precisar importar o "React" nas páginas.

    ```js
        module.exports = {
            presets: [
                '@babel/preset-env',
                ['@babel/preset-react', {
                    runtime: 'automatic'    // add
                }]
            ]
        }
    ```

    `yarn webpack` exculta o webpack.

5. Agora, no arquivo "index.js" na pasta "src", é só trocar o "h1" pelo componente "<App />".

    ```js
        import { render } from 'react-dom';
        import { App } from './App';

        render(<App />, document.getElementById('root'));
    ```

6. Corrigindo o Erro "mode" ('develoment' or 'production'). No arquivo "webpack.config.js", adicionar:

    ```js
        const path = require('path')

        module.exports = {
            mode: 'development',    // add
            ...
        }
    ```

