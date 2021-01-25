# 笔记

## 放大 git bash 的字体
ctrl + 滚轮

## cd 与 ls
* cd 切换文件夹(工作目录)
  * cd /c   绝对路径
  * cd www  切换到当前的 www 文件夹下
  * cd ..   切换到上一级目录
* ls 查看当前文件夹下的文件内容

## rm 
删除不会进回收站
```
//删库跑路
rm   -rf   /
```

## linux 命令运行潜规则
如果没有报错, 没有提醒, 表明执行『成功』

## .swp 是 vim 生成的临时文件

## 底线命令
* w write 写入保存
* q quit  退出

## 复制和粘贴(了解)
* ctrl + insert 复制
* shift + insert 粘贴

## 软件  (下载尽量到『官网』下载)
* 输入法.  QQ 输入法
  * win10 自带的剪切板功能 （win + v）
  * 中文状态下使用英文标点 (搜狗和 QQ 都有)
* https://www.processon.com/ 在线绘图工具
* utools 快速启动工具 (alt + 空格)  https://www.u.tools/
* clover 标签页形式的资源管理器     http://cn.ejie.me/
* typora 一款 markdown 的编辑器(目前最火)

## 查看暂存区文件列表
```
git ls-files
```

## status 状态
git status 查看当前 Git 仓库的状态

## 常见状态
```
On branch master    在 master 分支上
nothing to commit, working tree clean  没有什么需要提交, 工作树是干净的
```
工作区的所有的修改都已经提交

```
Untracked files:    未跟踪的文件(新的文件)
  (use "git add <file>..." to include in what will be committed)
        cart.html   
```
有新增文件

```
Changes to be committed:  以下修改将会被提交
  (use "git restore --staged <file>..." to unstage)
        new file:   cart.html
```
暂存区有新的修改, 可以使用 git commit 命令进行提交

```
Changes not staged for commit:  为登上舞台修改提交
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   app.css
        modified:   app.js
```
在工作区对这几个文件进行了内容修改.

## 关于颜色
* 红色   红色的文件 修改只存在于『工作区』
* 绿色   绿色的文件 此修改存在于『工作区与暂存区』


## git 常用操作总结
* git status  查看状态
* git add -A  添加至暂存区
* git commit  建立新的存档

## git diff
diff  ->  different  不同的

## .gitignore 一般放置在 .git 同级目录下

## 


































## 卸载密码管理工具
```
git credential-manager uninstall
```
