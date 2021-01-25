# MongoDB



## 简介

MongoDB 是为快速开发互联网Web应用而设计的数据库系统，官方地址 <https://www.mongodb.com/>

数据库（DataBase）是按照数据结构来组织、存储和管理数据的仓库。是一个应用程序



## 下载安装

下载地址 <https://www.mongodb.com/download-center/community>

安装过程截图

![1](assets/1.png)

![2](assets/2.png)

![3](assets/3.png)

![4](assets/4.png)

![5](assets/5-1574195521250.png)

![6](assets/6.png)

安装的默认位置

```
C:\Program Files\MongoDB
```

安装完毕后进行几步操作

一、为了方便在命令行下运行，可以配置 mongodb 命令的环境变量 PATH

此电脑 -> 属性 -> 高级系统设置 -> 环境变量 -> 双击 Path ->  新建 -> 设置 mongod.exe 所在文件夹路径

```sh
C:\Program Files\MongoDB\Server\3.2\bin
```

二、创建默认的仓库文件夹

```sh
c:\data\db
```

三、打开命令行窗口输入mongod 启动数据库服务器

![1574196036556](assets/1574196036556.png)

四、另起一个命令行运行 mongo 

![1574196149538](assets/1574196149538.png)



## 使用

### 三个重要概念

* 一个服务可以创建多个数据库
* 数据库（database） 数据库是一个仓库，在仓库中可以存放集合
* 集合（collection）    集合类似于JS中的数组，在集合中可以存放文档
* 文档（document）  文档数据库中的最小单位，类似于 JS 中的对象，在 MongoDB 中每一条数据都是一个 JS 的对象

![img](assets/clip_image002.jpg)

### 常用命令

#### 数据库集合命令

1) 显示所有的数据库

```sh
show dbs
show databases
```

2) （创建）切换到指定的数据库

```
use 数据库名
```

3) 显示当前所在的数据库

```
db
```

4)   删除当前数据库（先切换再删除）

```
use project_1
db.dropDatabase()
```

5)  显示当前数据库中的所有集合

```js
db.createCollection('users');     //创建集合
show collections
```

6)  删除当前集合

```js
db.collection.drop()
```

7)  重命名集合

```js
db.collection.renameCollection('newName')
```

> 操作集合时，如果集合不存在则会自动创建集合

#### 文档命令

1）插入文档

```
db.collection.insert(文档对象);
```

2)  查询文档

```
db.collection.find(查询条件)	
db.collection.findOne(查询条件)
```

3)  更新文档

```js
db.collection.update(查询条件,新的文档)   
// 更新一个
db.collection.updateOne(查询条件,要更新的内容) 
// 批量更新
db.collection.updateMany(查询条件,要更新的内容)
//eg
db.students.update({name:'xiaohigh'},{$set:{age:19}})
```

4)  删除集合中的文档

```
db.collection.remove(查询条件)
```

#### 条件控制

##### 运算符

在 mongodb 不能 > < >=  <= !== 等运算符，需要使用替代符号

* `>`   使用 `$gt`
* `<`   使用 `$lt`
* `>=`   使用 `$gte`
* `<=`   使用 `$lte`
* `!==`   使用 `$ne`

##### 逻辑或

`$in` 满足其中一个即可 

```
db.students.find({age:{$in:[18,24,26]}}) //  /[aedf]/  
```

`$or` 逻辑或的情况

```js
db.students.find({$or:[{age:18},{age:24}]});
```

`$and` 逻辑与的情况

```
db.students.find({$and: [{age: {$lt:20}}, {age: {$gt: 15}}]});
```

##### 正则匹配

条件中可以直接使用 JS 的正则语法

```js
db.students.find({name:/imissyou/});
```



## Mongoose

### 介绍

Mongoose 是一个对象文档模型（ODM）库，它对Node原生的MongoDB模块进行了进一步的优化封装，并提供了更多的功能。 官网 <http://www.mongoosejs.net/>

### 作用

使用代码操作 mongodb 数据库

### 使用流程

一、安装 mongoose

在命令行下使用 npm 或者其他包管理工具安装（cnpm  yarn）

```sh
npm install mongoose --save
```

二、引入包

在运行文件中引入 mongoose

```js
var mongoose = require('mongoose');
```

三、连接数据库

```js
mongoose.connect('mongodb://127.0.0.1:27017/data');

//如果启动时遇到警告提醒， 则按照提示增加选项即可
mongoose.connect('mongodb://127.0.0.1:27017/data', {useNewUrlParser: true, useUnifiedTopology: true});
```

四、监听连接事件

```js
mongoose.connection.on('open', function () {
	
	//下面编写数据库操作代码
    
    //五、创建文档结构
    var SongSchema = new mongoose.Schema({
        title: String,  //歌名
        author: String  //歌手
    });
    
    //六、创建文档模型
    var SongModel = mongoose.model('songs', SongSchema);
    
    //七、使用模型进行文档处理（这里以增加数据为例）
    SongModel.create({title:'野狼disco',author:'宝石gem'}, function(err,data){
        if(err) throw err; //这里判断错误
        
        //下面编写创建成功后的逻辑
        // ... ...
        
        //八、关闭数据库连接（可选，代码上线之后一般不加）
        mongoose.connection.close();
    });
	
});
```

### 数据类型

文档结构可选的字段类型列表

- ==String==
- ==Number==
- Date
- Buffer
- Boolean
- Mixed   任意类型（使用 mongoose.Schema.Types.Mixed 设置）
- ObjectId
- ==Array==
- Decimal128（4.3版本后加入）

### CURD

数据库的基本操作包括四个，增加（create），删除（delete），修改（update），查（read）

#### 增加

插入一条

```js
SongModel.create({
    title:'给我一首歌的时间',
    author: 'Jay'
}, function(err, data){
    //错误
    console.log(err);
    //插入后的数据对象
    console.log(data);
});
```

批量插入

```js
SongModel.insertMany([
    {
        title:'给我一首歌的时间',
        author: 'Jay'
    },
    {
        title:'爱笑的眼睛',
        author: 'JJ Lin',
    },
    {
        title:'缘分一道桥',
        author: 'Leehom Wang'
    }
], function(err, data){
    console.log(err);
    console.log(data);
});
```

#### 删除

删除一条数据

```js
SongModel.deleteOne({_id:'5dd65f32be6401035cb5b1ed'}, function(err, data){
    console.log(err);
    console.log(data);
});
```

批量删除

```js
SongModel.deleteMany({author:'Jay'}, function(err, data){
    console.log(err);
    console.log(data);
});
```

#### 更新

更新一条数据

```js
SongModel.updateOne({author: 'JJ Lin'}, {author: '林俊杰'}, function (err, data) {
    console.log(err);
    console.log(data);
});
```

批量更新数据

```js
SongModel.updateMany({author: 'Leehom Wang'}, {author: '王力宏'}, function (err, data) {
    console.log(err);
    console.log(data);
});
```

#### 查询

查询一条数据

```js
SongModel.findOne({author: '王力宏'}, function(err, data){
    console.log(err);
    console.log(data);
});
//根据 id 查询数据
SongModel.findById('5dd662b5381fc316b44ce167',function(err, data){
    console.log(err);
    console.log(data);
});
```

批量查询数据

```js
//不加条件查询
SongModel.find(function(err, data){
    console.log(err);
    console.log(data);
});
//加条件查询
SongModel.find({author: '王力宏'}, function(err, data){
    console.log(err);
    console.log(data);
});
```

##### 字段筛选

```js
SongModel.find().select({_id:0,title:1}).exec(function(err,data){
    console.log(data);
});
```

##### 数据排序

```js
SongModel.find().sort({hot:1}).exec(function(err,data){
    console.log(data);
});
```

##### 数据截取

```js
SongModel.find().skip(10).limit(10).exec(function(err,data){
    console.log(data);
});
```

## 图形化操作

![1](assets/1-1574519196603.png)

![2](assets/2-1574519223041.png)

![3](assets/3-1574519211809.png)

![4](assets/4-1574519235005.png)

![5](assets/5-1574519240818.png)





## 附录

###  mongodb 配置密码

一、启动 mongod 带验证选项

```sh
# mongod --auth    
```

二、创建用户

```sh
> use admin      # 固定写法
> db.createUser({user:"admin",pwd:"password",roles:["root"]})   # roles:['root'] 是固定的
```

三、连接 mongod 服务

```
> use admin
> db.auth("admin", "password")
1
```

四、mongoose 连接操作

```js
// authSource=admin  固定的
mongoose.connect('mongodb://admin:password@localhost/prepare?authSource=admin');
```



### 关系型数据库（RDBS）

代表有：MySQL、Oracle、DB2、SQL Server...

特点：关系紧密，都是表

![img](assets/clip_image002.png)

优点：

1、易于维护：都是使用表结构，格式一致；

2、使用方便：通用，可用于复杂查询；   

3、高级查询：可用于一个表以及多个表之间非常复杂的查询。  

缺点：

1、读写性能比较差，尤其是海量数据的高效率读写；

2、有固定的表结构，字段不可随意更改，灵活度稍欠；

3、高并发读写需求，传统关系型数据库来说，硬盘I/O是一个很大的瓶颈。

### 非关系型数据库（NoSQL   not  only  SQL ）

代表有：MongoDB、Redis...

特点：关系不紧密，有文档，有键值对



![nosql](assets/nosql.png)

优点：

1、格式灵活：存储数据的格式可以是key,value形式。

2、速度快：nosql可以内存作为载体，而关系型数据库只能使用硬盘；

3、易用：nosql数据库部署简单。

缺点：

1、不支持事务；

2、复杂查询时语句过于繁琐。

