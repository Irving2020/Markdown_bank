# 笔记

## loader npm的包
* load 加载
* loader 加载器
> loader 可以让 webpack 处理更多类型的模块
> webpack 默认只能处理 js json 模块.  对于 css less 图片 字体 webpack 默认不能处理, 借助 loader 可以将其他类型转化为 webpack 可以处理的模块

## cli
client 单词缩写, 命令行

## 局部安装打包
```
node ./node_modules/webpack/bin/webpack.js ./src/js/app.js -o ./build/js/bundle.js --mode=development  

npx webpack ./src/js/app.js -o ./build/js/bundle.js --mode=development
```

## vscode 左侧文件夹
设置 -> 搜索 -> compact Folders -> 取消勾选

## webpack 打包 css 文件过程
1. 安装 loader
```
npm i css-loader style-loader -D
```
2. 修改 webpack.config.js
```js
module.exports = {
    entry: 'xxx',
    module: {
        rules: [//规则
            {
                test: /\.css$/, //如果目标模块文件后缀是 .css
                use: [
                    //一定注意顺序, 运行顺序是自下而上的
                    'style-loader',
                    'css-loader'
                ]
            }
        ]
    }
}
```
3. 运行打包命令
```
npx webpack
```

## polyfill
温暖的填充物

## base64
是一种编码方式

## 注意
修改 webpack.config.js 之后, 一定要重新启动服务, 才能看到最新的效果

## 注意区分
* webpack-dev-server 用来启动一个HTTP服务, 一边修改代码一边查看效果
* webpack            用来打包文件

## 创建 HTTP 服务
* http-server

## HTTP 服务
不是只有浏览器可以向 HTTP 服务发送请求, 包含但不限于
* 浏览器
* Android APP
* IOS   APP
* 脚本语言 js  java  python  php  go   


