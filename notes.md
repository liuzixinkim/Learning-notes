##2016-11-19
##git
## 安装git
mac http://brew.sh
```
brew install git
```

## 配置git的使用者
```
git config --global user.name 'github的名字'
git config --global user.email 'github的邮箱'
```

## svn  git的区别
- svn集中式
- git分布式
## 查看配置列表
```
git config --list
```

## clear清屏

## 三个区
- 工作区 真实写代码的地方（开发项目时的目录）
- 暂存区/缓存区 把内容暂时存放一下(过渡作用)，将代码暂存后 一起提交出一个版本，维护版本库
- 历史区/版本库 放到版本库中的东西永远不会丢失

> github 远程仓库（历史区，最终展式的内容肯定是某一个版本）

## cd (change directory) 改变目录
- 使用gitbash 切换盘符需要加cd cmd中直接盘符:

## 初始化git仓库
表示当前文件夹下归git所管理
```
git init
```
## 删除目录
```
rm -rf 文件夹名字
```
## 查看文件夹
包括隐藏文件
```
ls -al 
```
## pwd打印目录
## 编辑文件内容
```
vi index.txt
```
- 进入编辑模式 i
- 退出编辑模式 ESC+ :WQ
## cat 查看文件内容
```
cat index.txt
```
## 像文件内输出内容
如果文件不存在则创建 如果多次echo > 会覆盖掉原有的内容
```
echo hello world > index.txt
```

> 两个大于号表示追加内容

## 查看状态 
```
git status
```
## 添加到暂存区中
```
git add 文件名
git add .
git add -A
```

## 将文件提交到历史区中
```
git commit -m"提交的内容"
``` 
## 查看git的提交日志
每次提交会产生一个版本号，存着对应的内容，切换版本号，就可以切换内容
```
git log
```
## 代码比较
- 工作区和暂存区的比较
```
git diff
```
- 工作区和历史区的比较
```
git diff master
```
- 暂存区和历史区的比较
```
git diff --cached
```

## 从工作区提交到历史区一步到位
不支持首次提交
```
git commit -a -m'ok'
```

## 让暂存区回到上次的add
```
git reset HEAD 文件名
```

## 用暂存区中的内容覆盖掉工作区的内容
```
git checkout 文件名
```

## 回滚 
- 回到过去
```
git reset --hard 版本号
```
- 站在过去角度回到未来
使用reflog查看所有操作
```
git reflog
git reset --hard 版本号
```

> 显示成一行需要加 --oneline

## 连接远程仓库
```
git remote add 名字 地址
```
- 查看配置的远程地址
```
git remote -v
git remote rm 名字 //删除远程地址
```

## 推送到远程仓库上
如果增加-u 下次再提交的时候就可以git push/git pull
```
git push origin master
-u upstream
``` 

## 创建忽略文件
创建一个文件叫.gitignore 里面写上不想要的文件

## 修改了本地的文件和修改了线上的文件
改的是同一个文件
- 为了防止在pull时拉取线上代码，覆盖掉本地内容，所以先要将本地的代码进行提交
- 在取拉取文件，拉取线上代码发现和本地冲突，此时不能自动合并，需要手动合并

> 修复冲突需要修改文件中=====<<<<<>>>> 将此类符号删掉保留想要的内容即可

## gh-pages
(如果把代码提交到这个分支上，guthub会给你个地址可以直接访问这个项目)
``` 
git push origin gh-pages
```

## 创建分支
- 创建分支
```
git branch gh-pages
```
- 切换分支
```
git checkout gh-pages
```
## 删除分支
切换到其他分支进行删除
```
git branch -d gh-pages
```
>删除该master命令： rm -rf .git
## 查看分支
```
git branch
```
## 推送分支
```
git push origin gh-pages
```
## 合并分支 
合并分支在主干合并其他分支
```
git merge gh-pages
```

> 一般情况下我们会将开发的内容建立一个开发分支将代码提交到开发分支上上线的时候合并到master分支，最后删除我们开发的分支即可

##
##2016-11-20
##node
- 概念
    - node是一个让js运行在浏览器外的服务器端的平台
    - 文件系统 模块 包 操作系统API 网络通信 
    - 摒弃传统的多线程 采用单线程、异步式I/O 事件驱动
- 优点
   - 基于js
   - 统一公共类库 代码标准化
   - 同步的 可以马上拿到返回值 异步函数都有回调函数
- 什么是IO
    - input 输入 从文件系统中读取文件
    - O 向文件系统写入文件
- 在node中的this是global
    - 直接console.log(this)是global 因为文件外边套了一层函数  改变了this 
    
## npm(依赖管理 node package manager 管理后台的文件)
- 记录依赖
初始化记录的依赖的文件 package.json
```
npm init
```
- 安装
    - 本地安装
        - 开发依赖(开发的时候使用，上线后不需要)
        ```
         npm install gulp --save-dev
        ```
        - 发布依赖(开发时候用，上线时仍需要)
        ```
         npm install jquery --save
        ```
    - 通过package.json来安装所需的依赖
        ```
        npm install
        ```
       > 默认安装到当前目录下的node_modules文件夹下
    
    - 全局安装(安装后可以在命令行下使用，比如gulp，默认安装到c盘下，不是所有文件都能全局安装的)
        安装后可以在命令行下使用
        ```
           npm install gulp -g
        ```
        > 全局安装不会安装到自己的文件夹中，查看全局安装的路径 npm root -g
- 卸载
    - 本地的卸载
    ```
    npm uninstall gulp --save-dev
    ```
    ```
    npm uninstall gulp --save 
    ```
    >--save-dev加上这个 在package.json也进行记录的删除
    - 全局卸载
    ```
    npm uninstall gulp -g
    ```
    - 查看全局的安装路径
    ```
    npm root -g
    ```
- 发布第三方包
    - 我们写好一个包，发布到npm上，包里必须要有package.json文件 
    ```
    npm init -y
    ```
     - 写一个包的入口文件 index.js
     - 确保源在npm上 查看源 nrm ls
     - 添加用户 (如果有表示已经登录)
     ```
     npm adduser
     ```
     >查看用户名 npm whoami  
     - 发布
     ```
     npm publish
     ```
     - 卸载发布
     ```
     npm unpublish --force
     ```
- 下载第三方包
    - 下载
    ```
    npm install 包名 --save
    ```
    - 引用第三方包 node_module必须在同级或者上级才能找到 会默认执行package.json文件中main指定的文件
    ```
    require(引用包的名字)
    ```
    >引用第三方别人发布上去的包 会自动在当前目录下node_moules下找对应的package.js文件中对用的main文件，默认是index.js，如果找不到，会向上一级找跟目录 找不到则报错
- 核心模块
    - 不用下载直接引用 http url fs path util 等
        - util中有一个继承的方法

## 源npm 切换源切换到国内
- cnpm taobao 
- 安装nrm工具，想在命令行下切换源
```
npm install -g nrm
```
- 显示所有源
```
nrm ls
```
- 添加源
```
nrm add zhufeng http://172.18.0.199
```
- 切换源
```
nrm use zhufeng
``` 
- 查看源网速
```
nrm test
```

## 安装nodeppt
```
npm install -g nodeppt
```
- 创建一个.md文件
- 开始写ppt
```
[slide]
##1
[slide]
##2
[slide]
##3
```
>必须采用markdown格式
- 命令行执行
```
nodeppt start
```
- 如果端口被占用重新指定端口
```
nodeppt start -p 3000
```
> 使用文档 https://github.com/ksky521/nodePPT
