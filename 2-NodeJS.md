# 笔记

## 扩展运算符
扩展运算符可以展开『实现了迭代器的数据』

## where 命令
用来定位命令的位置

## nodeJS 安装 2503 报错
是因为权限不足, 解决的方法
```
https:www.cnblogs.com/cpqwebfe/p/10278097.html
1. 命令提示符 -> 管理员身份打开
2. cd 到安装文件所在位置
3. msiexec 安装包名字
```
## nodeJS 运行文件的步骤
1. 打开命令行
2. 将命令行的工作目录定位到 JS 文件夹下
     * d:   切换盘符
     * cd   切换文件夹命令
     * dir  查看文件夹下的文件列表
3. 运行文件
      node 文件名

## windows cmd 命令行复制粘贴
* 复制 选中内容 -> 点击右键
* 粘贴 不选中内容 -> 点击右键

## 快速打开指定文件夹的命令行
1. 资源管理器打开指定的文件夹
2. 在路径导航部分 -> 鼠标单击 -> 变成可编辑状态
3. 输入 cmd -> 敲回车

## 编辑器集成的命令行
在指定的文件夹右键 -> 在集成终端中打开

## windows 下 C 盘的特殊文件夹

## ASCII 字符与数字的转换
```
console.log('a'.charCodeAt())//通过字符获取在 ASCII 中的编号
console.log(String.fromCharCode(105));//通过数字获取对应的符号
```

## fs.writeFile
* 不能直接在 c 盘的根目录下写入文件
* 路径所涉及的文件夹, 必须存在, 如果不存在写入会失败

## mode
0o666 文件的权限   

* 6 所有者的权限
* 6 所属组的权限
* 6 其他人的权限

* 4   可读
* 2   可写
* 1   可执行

777  文件的文件的最高权限 

## flag 旗帜
* a   append 追加
* w   write  写入
* r   read   只读

## 写入文件的场景
当需要持久化保存数据的时候, 想到『写入文件』

## 写入文件两种方式
* writeFile 简单写入  应对简单的内容写入, 次数较少
* createWriteStream  应对批量内容写入

## 读取文件的方式选择
* 对于小文件的读取   readFile 
* 对于大文件读取     createReadStream 

## 软件推荐
* everything 快速搜索工具
* treeSizeFree 查看文件夹大小
* IDM 网页下载工具
* https://www.yunpanjingling.com/  云盘精灵
