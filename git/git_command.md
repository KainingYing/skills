# Git指令

## 1. 配置git

```
# 添加配置
git config --global user.name "yourName" 
git config --global user.email "youEmailAddress"

# 删除
git config --global --unset user.name "yourName"
git config --global --unset user.name "yourName"

# 可以在 C盘 --> use(或用户) --> 电脑用户 --> .gitconfig 查看是否修改完成
# 查看
git config user.name
git config user.email
git config --global -l # 显示所有的配置
```

## 2. 创建版本库

```
# 初始化版本库，会添加一个叫.git的文件
git init

# 添加文件到仓库，分两步走
git add <file>
# 一次提交多个add
git commit -m <message>
```

## 3. 版本穿梭

```
# 查看工作区情况，可以查看文件被修改的情况，也就是暂存区的情况
git status
# 查看文件修改内容
git diff <file>

# 显示从最近到最远的提交日志
git log 
git log --pretty=online  # 精简地显示

git reset
# Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交1094adb...（注意我的提交ID和你的肯定不一
# 样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
# git reset --hard HEAD^

git reflog可以查看历史指令，以便回到未来
```

## 4.工作区和暂存区

## 5.删除文件

```
# 将文件从工作区删除以后，也在版本库中进行删除
git rm <file> 

# git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”
git checkout -- <test.txt> 
```

## 6. 分支管理

```
git checkout -b <branch>
# 上面这条指令完成创建分支以及切换分支
git branch <branch>
git checkout <branch>

# 查看当前分支
git branch
```

## 7. 标签管理

```
git tag <tag_name>  # 将tag_name这个标签打在最新的一次commit上
git tag # 查询所有标签
```



# Github

## 1. 建立ssh连接

```
# 查看~/.ssh里面有没有id_rsa和id_rsa.pub两个文件，没有的话执行以下程序
ssh-keygen -t rsa -C "youremail@example.com"

# 接下来步骤可以参考https://blog.csdn.net/u013778905/article/details/83501204
```

## 2. 远程仓库需要用到的指令

```
git clone <url>
git remote add origin <https://github.com/yingkaining/mygit.git>  # 添加远程服务器
git push -u origin master
git pull origin master
git fetch
```

## 3. 提交PR

```
# step1: fork一个想要的仓库
# step2: 将fork到的仓库进行clone至本地
# step3: 建立连接,可以使用git remote -v进行查看，修改远程仓库可以使用git remote add origin <url>
# step4: 修改文件以后使用git add+git commit+git push到远程仓库
# step5: 在github上提交PR
# step6: 等待作者merge
```

# Q&A

**Q**: warning: LF will be replaced by CRLF in readme.txt. The file will have its original line endings in your working directory.

**A**：以下解答来自[知乎](https://zhuanlan.zhihu.com/p/380574688).

**Q**: OpenSSL SSL_connect: Connection was reset in connection to github.com:443

**A**：参考[博客](https://blog.csdn.net/qq_37555071/article/details/114260533)，使用方法二成功解决。

```
# 将端口号（1080）设置为自己的端口号
git config --global http.proxy 127.0.0.1:1080
git config --global https.proxy 127.0.0.1:1080
```

