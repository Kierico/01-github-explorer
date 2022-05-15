# Importando Arquivos CSS

1. Adicionar no arquivo "webpack.config.js", mais uma regras (rules):

    ```js
        module.exports = {
            ...
            module: {
                rules: [
                    {
                        test: /\.jsx$/,
                        exclude: /node_modules/,
                        use: 'babel-loader',
                    },
                    {   // add
                        test: /\.css$/,
                        exclude: /node_modules/,
                        use: ['style-loader', 'css-loader'],
                    }
                ],
            }
        };
    ```

2. Instalar dois loaders `yarn add style-loader css-loader -D`, precisa ser os dois, pois eles trabalham em conjunto para entender os arquivos CSS.

3. `yarn dev`

