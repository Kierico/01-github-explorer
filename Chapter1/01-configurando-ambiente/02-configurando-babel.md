# Babel

    Serve para converter o código, para que todo browser e todo ambiente da aplicação, consiga entender todos os códigos.

[ <img style="width: 100px;" src="https://d33wubrfki0l68.cloudfront.net/7a197cfe44548cc1a3f581152af70a3051e11671/78df8/img/babel.svg"> ](https://babeljs.io/)

## Instalar Babel

1. `yarn add @babel/core @babel/cli @babel/preset-env -D`

2. Crie um arquivo "babel.config.js".

    ```js
        module.exports = {
            presets: [
                '@babel/preset-env'
            ]
        }
    ```

    menu de ajuda: `yarn babel -h`, vem do "@babel/cli".

3. Crie um arquivo "index.js" dentro de "src".

    ```js
        import React from 'react';

        function App() {
            return <h1>Hello Word</h1>
        }
    ```

4. `yarn babel src/index.js --out-file dist/bundle.js`


5. Instalar para endenter o código react utilizado.

    5.1 `yarn add @babel/preset-react -D`

6. Adicinar no arquivo "babel.config.js"

    ```js
        module.exports = {
            presets: [
                '@babel/preset-env',
                '@babel/preset-react'   // add
            ]
        }
    ```

7. Trocar extensão ".js" para ".jsx" do arquivo "index.js" na pasta "src".

8. `yarn babel src/index.jsx --out-file dist/bundle.js`

