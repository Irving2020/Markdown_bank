# 笔记

## 小电影网站过程
1. 准备数据
2. HTML 布局
3. 搭建 HTTP 服务(express框架)
   1. 路由规则
   2. 根据 id 读取电影信息, 显示电影详情页面


## set-cookie
是服务器响应 cookie 信息的『响应头』

## path=/
path 路径
```
set-cookie: name=xiaohigh; path=/; domain=.baidu.com; HttpOnly
```
* path 设置该 cookie 生效的路径  
* /  根目录
* domain 该 cookie 生效的域名   www.baidu.com   music.baidu.com 
* HttpOnly 表明该 cookie 只能进行 HTTP 请求使用. 此标识表明该 cookie 不允许浏览器通过 JS 修改此cookie的值 (document.cookie)

## 声明周期
1. 设置时间的 cookie
   时间一到, 就过期, 访问时就不携带发送请求, 关闭浏览器不销毁
2. 不设置时间的 cookie
   关闭浏览器, 该 cookie 就会过期

## session 和 cookie 作用
记录保存『当前用户』的相关信息
* 邮箱 用户名 头像 
* 验证码
* 权限

## 使用场景 (session)
1. 登录 身份校验
2. 验证码的保存
3. 权限的保存

## cookie
浏览器之间 cookie 是不共享的



