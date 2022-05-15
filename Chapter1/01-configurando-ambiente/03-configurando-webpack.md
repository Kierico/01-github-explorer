# Webpack

    Vai converter (looders) os arquivos para ser entendido pelos browsers. Ex: ".sass" para ".css".
    Modules With Dependencies ---> Static Assets.

[ <img style="width: 100px;" src="https://webpack.js.org/site-logo.1fcab817090e78435061.svg"> ](https://webpack.js.org/)

## Instalar Webpack

1. `yarn add webpack webpack-cli -D`

2. Crie um arquivo "webpack.config.js":

    ```js
        /** de acordo com o sistema operacional */
        const path = require('path')

        module.exports = {
            /** qual é o arquivo principal (inicial, entrada) da aplicação */
            entry: path.resolve(__dirname, 'src', 'index.jsx'),

            /** qual é o arquivo que vai ser gerado com o webpack */
            output: {
                path: path.resolve(__dirname, 'dist'),
                filename: 'bundle.js'
            },
            resolve: {
                extensions: ['.js', '.jsx'],
            },
            module: {
                rules: [
                    {
                        /** $ = que o arquivo deve terminar com ".jsx". */
                        test: /\.jsx$/,

                        /** exclui porque é responsabilidade da biblioteca que esta sendo utilizada á conversão do arquivo. */
                        exclude: /node_modules/,

                        /** converte o arquivo para que o browser entenda. */
                        use: 'babel-loader',
                    }
                ],
            }
        };
    ```

3. `yarn add babel-loader -D`

    babel-loader é a integração do "Babel" com o "Webpack".

4. Crie um arquivo "App.jsx" na pasta "src":

    ```js
        export function App() {
            return <h1>Hello World</h1>
        }
    ```
E... importe para o arquivo "index.jsx" em "src":

    ```js
        import { App } from './App';
    ```

5. `yarn webpack`

    Excutar o webpack.

