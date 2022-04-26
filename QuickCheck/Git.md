#### 在git bash中为本地机器设置所有仓库用户信息
>git config --global user.name "[name]"

>git config --global user.email "[email address]"

#### 在文件目录下初始化本地仓库（当前文件夹就是一个本地Repo）
>git init

添加要提交的内容
> git add

将内容记录提交至本地仓库
>git commit -m "说明"
---

#### 关联远程github
生成本地sshkey
>ssh-keygen -t -rsa -C "likakayang@yeah.net"

将公钥id_rsa.pub复制粘贴到github

#### 远程仓库同步（和github仓库同步）
>git remote add origin git@github.com:likakayang/myNote.git

删除远程仓库地址
>git remote rm origin

同步本地到远程仓库
>git push -u origin master

后续同步
>git push origin master

---
## git相关指令
### 为所有的本地仓库配置用户信息

> $git config --global user.name "[name]"

设置用户名作为提交事务方的责任人

> git config --global user.email "[email address]"

设置邮箱作为提交事务方的联系方式

> ssh-keygen -t rsa -C "likakayang@yeah.net"

生成本地ssh key文件

> ssh-agent bash(可以不用，直接输入下一条命令，如果出错，加上这条)
>
> ssh-add id_rsa(包括文件路径)

将秘钥添加到本地git

> $git config ---global color.ui.auto

开启命令行颜色提示功能

### 创建一个新仓库并从已有的url获取目标项目

> $git init [project-name]

创建一个特定名字的本地仓库

> $git clone [url]

克隆一个项目及其历史版本信息

### 检查编辑与处理提交事务

> $git status

罗列要提交的文件清单，包括新文件与更改的文件

> $git diff

比较工作文件与快照的不同之处

> $git add [file]

为版本文件生成快照

> $git diff --staged

显示上个版本与本地仓库文件的不同

> $git reset [file]

不对文件进行阶段性处理，但是保存其内容

> $git commit -m "[descriptive message]"

在版本历史中永久记录文件快照

###  分支管理

> $git branch

列出当前仓库所有的本地分支

> $git branch [branch-name]

创建一个新分支

> #git checkout [brach-name]

切换到指定分支并更新工作目录

> $git merge [branch]

结合指定分支的历史到当前分支

> $git branch -d [branch-name]

删除指定分支

### 迁移和删除版本文件

> git rm [file]

从工作目录删除文件并且缓存删除内容

> git rm --cached [file]

从版本控制系统中移除文件但保留本地的

> $git mv [file-original] [file-renamed]

更改文件名字准备提交

### 避免临时文件和路径引起冲突

> *.log
>
> build
>
> temp-*

名为“.gitignore”的文件可以防止临时文件、路径与正式版本冲突

> $git ls-files --other --ignored --exclude-standard

列出所有在项目中被忽略的文件

### 搁置或恢复不完全的更改

> $git stash

随时保存修改的文件

>$git stash pop

恢复最近被存储起来的文件

> git stash list

列出所有变更的合集

> $git stash drop

丢弃最近被封锁的变更集

### 浏览和查看项目文件的变更

> $git log --follow [file]

罗列指定文件的版本信息

> $git diff [first-branch]...[second-branch]

显示两个不同分支的区别

> $git show[commit]

显示某次提交的元数据以及内容更改

### 消除错误，手动更改历史

> $git reset [commit]

撤销指定提交之后的所有提交，保留本地更改

> $git reset --hard[commit]

丢弃所有的历史以及更改，回滚至指定提交

### 注册一个仓库并交换版本信息

> $git fetch [bookmark]

从被bookmark标记的仓库下载所有的历史

> $git merge [bookmark]/[branch]

将bookmark分支的内容融合进当前本地分支

> $git push [alias] [branch]

提交所有的本地分支至github

> $git pull

下载bookmark历史并整合更改

[参考文档](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)