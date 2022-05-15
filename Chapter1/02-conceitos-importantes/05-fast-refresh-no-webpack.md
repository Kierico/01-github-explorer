# Fast Refresh

[ <img style="width: 100px;" src="https://github.com/pmmmwh.png"> ](https://github.com/pmmmwh/react-refresh-webpack-plugin)

1. Install

    ### if you prefer npm
    `npm install -D @pmmmwh/react-refresh-webpack-plugin react-refresh`

    ### if you prefer yarn
    `yarn add -D @pmmmwh/react-refresh-webpack-plugin react-refresh`

    ### if you prefer pnpm
    `pnpm add -D @pmmmwh/react-refresh-webpack-plugin react-refresh`

2. Adicionar no arquivo "webpack.config.js":

    ```js
        const path = require('path');
        const HtmlWebpackPlugin = require('html-webpack-plugin');
        const ReactRefreshWebpackPlugin = require('@pmmmwh/react-refresh-webpack-plugin');  // add

        const isDevelopment = process.env.NODE_ENV !== 'production';

        module.exports = {
            mode: isDevelopment ? 'development' : 'production',
            devtool: isDevelopment ? 'eval-source-map' : 'source-map',
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
                hot: true,  // add
            },
            plugins: [
                /** só add se estiver no modo de desenvolvimento */
                isDevelopment && new ReactRefreshWebpackPlugin(),   // add
                new HtmlWebpackPlugin({
                    template: path.resolve(__dirname, 'public', 'index.html')
                })
            ].filter(Boolean),  // add
            module: {
                rules: [
                    {
                        test: /\.jsx$/,
                        exclude: /node_modules/,
                        use: {  // add
                            loader: 'babel-loader',
                            options: {
                                plugins: [
                                    isDevelopment && require.resolve('react-refresh/babel')
                                ].filter(Boolean)
                            }
                        },
                    },
                    {
                        test: /\.scss$/,
                        exclude: /node_modules/,
                        use: ['style-loader', 'css-loader', 'sass-loader'],
                    }
                ],
            }
        };
    ```

`Ctrl+C`, para parar a aplicação.

`yarn dev` para iniciar a aplicação.

