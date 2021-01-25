## NPM

### 介绍

全称：Node Package Manager , Node 的包管理器，也是一个应用程序。

### 包是什么

Node.js 的包基本遵循 CommonJS 规范，将一组相关的模块组合在一起，形成一个完整的工具

### 作用

通过 NPM 可以对 Node 的工具包进行搜索、下载、安装、删除、上传。借助别人写好的包，可以让我们的开发更加方便。

### 安装

安装完 nodejs 之后会自动安装 npm

### 常用命令

#### 查看 npm 的版本

```sh
npm -v 
```

#### 初始化

```sh
npm init
npm init --yes
```

运行后会创建 package.json 文件             

```json
{
  "name": "1-npm",      #包的名字
  "version": "1.0.0",   #包的版本
  "description": "",    #包的描述
  "main": "index.js",   #包的入口文件
  "scripts": {			#脚本配置
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",			#作者
  "license": "ISC"		#版权声明
}
```

> ==注意生成的包名不能使用中文，大写 ！！！ 不能使用 npm 作为包的名字==

关于开源证书扩展阅读

<http://www.ruanyifeng.com/blog/2011/05/how_to_choose_free_software_licenses.html>

#### <span style="color:blue">搜索包</span>

```sh
npm search jquery
npm s jquery
```

一般在搜索工具包的时候，会到 https://npmjs.org 搜索

#### 安装工具包

```sh
npm install jquery
npm i jquery

# 安装并在 package.json 中保存包的信息(dependencies 属性)
npm install jquery --save
npm install jquery -S

# 安装并在 package.json 中保存包的信息(devDependencies 属性)
npm install babel --save-dev
npm install babel -D

```

>  6 版本的 npm ，安装包时会自动保存在 dependencies 中，可以不用写 --save

#### 全局安装

```sh
npm install less -g
npm install nodemon -g 
```

全局安装一般用于安装全局工具，如 cnpm，yarn，webpack ，gulp等，全局命令的安装位置

```
C:\Users\你的用户名\AppData\Roaming\npm
```

> 全局安装命令在任意的命令行下, 都可以执行

#### 安装依赖

根据 package.json 中的依赖声明， 安装工具包

```sh
npm i
npm install
npm i --production // 只安装 dependencies 中的依赖
```

#### 移除包

```sh
npm remove jquery
```

### 使用流程

团队开发时使用流程

1. 从仓库中拉取仓库代码
2. ==运行 npm install 安装相关依赖==
3. 运行项目，继续开发

### 封装 NPM 包

创建自己的 NPM 包可以帮助代码进行迭代进化，使用步骤也比较简单

0. 修改为官方的地址 (npm config set registry https://registry.npmjs.org/)

1. 创建文件夹，并创建文件 index.js， 在文件中声明函数，使用 module.exports 暴露
2. npm 初始化工具包，package.json 填写包的信息
3. 账号注册（激活账号）,==完成邮箱验证==
4. 命令行下 『npm login』 填写相关用户信息
5. 命令行下『 npm publish』 提交包 👌

> npm 有垃圾检测机制，如果名字简单或做测试提交，很可能会被拒绝提交
>
> ==可以尝试改一下包的名称来解决这个问题==

升级 NPM 包，需要修改 package.json 中的版本号修改，只需要执行『npm publish』就可以能提交

1. 修改包代码
2. 修改 package.json 中版本号
3. npm publish 提交

### 删除 npm 包

```
npm unpublish 包名 --force
```

### CNPM

#### 介绍

cnpm 是淘宝对国外 npm 服务器的一个完整镜像版本，也就是淘宝 npm 镜像，网站地址<http://npm.taobao.org/>

#### 安装

安装配置方式有两种

* npm install -g cnpm --registry=https://registry.npm.taobao.org
* alias cnpm="npm --registry=https://registry.npm.taobao.org \
  --cache=$HOME/.npm/.cache/cnpm \
  --disturl=https://npm.taobao.org/dist \
  --userconfig=$HOME/.cnpmrc"       (只能在Linux下使用)

#### 使用

配置完成后，就可以使用 cnpm 命令来管理包，使用方法跟 npm 一样

```sh
cnpm install lodash
```

#### npm 配置镜像地址

```sh
//淘宝镜像
npm config set registry https://registry.npm.taobao.org
//官方镜像   
npm config set registry https://registry.npmjs.org/
```

> 在发布工具的时候, 一定要将仓库地址, 修改为官方的地址

### Yarn

#### 介绍

yarn 是 Facebook 开源的新的包管理器，可以用来代替 npm。

#### 特点

yarn 相比于 npm 有几个特点

* 本地缓存。安装过的包下次不会进行远程安装
* 并行下载。一次下载多个包，而 npm 是串行下载
* 精准的版本控制。保证每次安装跟上次都是一样的

#### 安装

##### yarn 安装

只需要一行命令即可安装 yarn

```sh
npm install yarn -g
```

##### msi 安装包安装

<https://classic.yarnpkg.com/en/docs/install#windows-stable>

#### 相关命令

yarn 的相关命令

1)  yarn --version

2)  yarn init  //生成package.json   

3)  yarn global add  package (全局安装)

​	全局安装路径 `C:\Users\你的用户名\AppData\Local\Yarn\bin`

4)  yarn global remove less (全局删除)

5)  yarn add package (局部安装)

6)  yarn add package --dev (相当于npm中的--save-dev)

7)  yarn remove package

8)  yarn list //列出已经安装的包名 用的很少

9)  yarn info packageName //获取包的有关信息  几乎不用

10)  yarn //安装package.json中的所有依赖 

> npm 5 引入离线缓存，提高了安装速度，也引入了 package-lock.json 文件增强了版本控制

yarn 修改仓库地址

```sh
yarn config set registry https://registry.npm.taobao.org
```

### CYarn

跟 npm 与 cnpm 的关系一样，可以为 yarn 设置国内的淘宝镜像，提升安装的速度

```sh
npm install cyarn -g --registry "https://registry.npm.taobao.org"
```

配置后，只需将yarn改为cyarn使用即可

### 附录

#### 关于版本号

版本格式：主版本号.次版本号.修订号

* "^3.0.0" ：锁定主版本，以后安装包的时候，保证包是3.x.x版本，x默认取最新的。
* "~3.2.x" ：锁定小版本，以后安装包的时候，保证包是3.1.x版本，x默认取最新的。
* "3.1.1" ：锁定完整版本，以后安装包的时候，保证包必须是3.1.1版本。

安装指定版本的工具包

```shell
yarn add jquery@1.11.2
```

#### npm 清除缓存

```
npm cache clean
```

