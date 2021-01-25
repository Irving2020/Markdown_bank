# 笔记

## GitHub 代理工具
```
https://github.com/bannedbook/fanqiang
```

## 异步操作
1. 定时器
2. 文件系统 
3. 数据库操作
```
mongoose.connection.on('open', ()=>{
    UserModel.create({}, (err, data) => {

    })
})
```
4. AJAX 请求回调

## promisify 
可以将 fs 模块中的异步的 API, 转化成返回 promise 对象形式的函数

## 状态
* fulfilled 是 Promise 对象成功的状态, 
* rejected  是 Promise 对象失败的状态

## resolve reject 函数
```
let p = new Promise((resolve, reject) => {
    <!-- resolve('ok'); -->
    resolve('error');
});
```
* resolve 执行, 改变了 p 对象的状态(*PromiseState*)『fulfilled』, 设置 p 对象成功的结果值(*PromiseResult*)为 『ok』
* reject 执行, 改变了 p 对象的状态(*PromiseState*) 『rejected』 , 设置 p 对象失败的结果值(*PromiseResult*)为 『error』

## 执行器函数
执行器函数中可以是『同步任务』, 也可以是『异步任务』