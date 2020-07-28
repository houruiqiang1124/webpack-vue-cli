# webpack-vue-cli

> webpack从0开始构架一个简易的vue脚手架项目

## 初始化package.json
    npm init

## 安装依赖
    npm install --save-dev webpack
    npm install --save-dev webpack-cli      // webpack 4+ 版本，需要安装 CLI

## 创建所需文件
    src/main.js
    webpack.config.js
    index.html

## NPM 脚本,在package.json的scripts添加属性
    "build": "webpack"
这时候运行npm run build就能看到目录下多出了dist文件夹，里面有个bundle.js


## DevServer, 使用DevServer,提供http服务，实时预览
    cnpm i -D webpack-dev-server

    在package.json的scripts增加npm脚本
    "dev": "webpack-dev-serve"

    npm run dev
    访问 localhost:8080

###  source-map
   --devtool source-map
   启动增加参数，用作断点调试

### 模块热替换
    --hot
    在不重新加载整个网页的情况下，通过将被更新过的模块替换老的模快

### host
    局域网中的其它设备访问你本地的服务，可以在启动 DevServer 时带上 --host 0.0.0.0。 host 的默认值是 127.0.0.1 即只有本地可以访问 DevServer 的 HTTP 服务

### port
    默认使用 8080 端口。 如果 8080 端口已经被其它程序占有就使用 8081，如果 8081 还是被占用就使用 8082，以此类推


## 使用vue框架，接入 Webpack
    npm i -S vue

    npm i -D vue-loader css-loader vue-template-compiler

    npm i -D style-loader css-loader

    cnpm i vue-loader-plugin -S     // vue-loader是 15之后的版本，需要安装一个叫做 VueLoaderPlugin 的插件

    cnpm install --save-dev mini-css-extract-plugin     // 在webpack4中，建议用mini-css-extract-plugin替代

### 修改 Webpack 相关配置
```
    module: {
        rules: [
            {
                test: /\.vue$/,
                use: ['vue-loader']
            },
            {
                // 用正则去匹配要用该 loader 转换的 CSS 文件
                test: /\.css$/,
                use: [MiniCssExtractPlugin.loader, 'css-loader'],
            }
        ]
    },
    plugins: [
        new MiniCssExtractPlugin({
            filename: `[name].css`,
        }),
        new VueLoaderPlugin({})
    ]
```

## 为单页应用生成 HTML
    cnpm install --save-dev html-webpack-plugin

webpack.config.js

    const HtmlWebpackPlugin = require('html-webpack-plugin');
    plugins: [
        new MiniCssExtractPlugin({
            filename: `[name].css`,
        }),
        new VueLoaderPlugin({}),
        new HtmlWebpackPlugin({
            filename: 'index.html',
            template: 'index.html',
            inject: true
        })
    ]

## 所用文档链接
[深入浅出 Webpack](http://www.xbhub.com/wiki/webpack/)

[webpack中文文档](https://www.webpackjs.com/concepts/)
