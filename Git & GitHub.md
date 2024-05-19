# <center><font face="微软雅黑" color=orange>Git & GitHub</font></center>

## 1.Git/GitHub是什么?
- **Git**
一个分布式版本控制系统,可以追踪文件的变化，允许多人协作开发，以及管理大型项目的版本控制 
<br>
- **GitHub**
  一个基于 Git 的代码托管平台，提供了代码仓库托管、版本控制、协作开发、项目管理等功能

## 2.Git相关
- **版本控制系统**
>集中式，如SVN,CVS
>>特点：一个中央服务器,多个client
>>缺陷：受限于中央服务器，中心服务器崩，多个崩
>
>分布式,如git
>>特点：本地有完整的代码库，分享、同步速度快

- **git安装和配置**
>安装完之后，可以使用 git -v，检查一下版本

>使用方式
>>cmd
>>GUI
>>IDE拓展

>配置
>>配置用户名：git config --global user.name moyuxia 
>>配置邮箱：git config --global usr.email 347232215@QQ.COM
>>配置Git 在处理远程仓库认证信息时使用存储凭据的方式(命令会将认证信息保存在本地计算机上的一个文件中，以后访问远程仓库时会自动使用这些凭据，无需每次输入用户名和密码):git config --global credential.help store
>>查看配置信息: git config --global --list

- **新建仓库**
>本地创建
>>mkdir newRepo
>>cd newRepo
>>git init
>>ls -a(显示所有文件和目录)
>>cd .git(进入.git文件)
>创建仓库时也可以指定名称：git init myRepo(myRepo为仓库)
>
>克隆仓库
>>git clone '仓库地址'

- **工作区域 & 文件状态**
>工作区域
>>工作区
>>>本地电脑目录
>>>查看工作区 ls
>
>>暂存区
>>>临时存储区域，用于保存即将提交到Git仓库的更改
>>>查看暂存区 git ls-files
>
>>本地仓库
>
> 文件状态
>>Untrack(未跟踪) - 新创建未被Git管理起来的文件
>>Unmodified(未修改) - 被Git管理起来但是文件未发生变化
>>Modified(已修改) - 已修改但未加入到暂存区
>>Staged(已暂存) -已修改并添加到暂存区

- **添加和提交文件**
>echo '第一个文件'> file1.txt(然后使用git status)
>git status - 查看当前仓库状态
>cat file1.txt(显示文件内容)
>git add *.txt / git add .
>git commit --m 'first commit'(提交到本地仓库)
>git log/git log --oneline(查看仓库提交记录/简洁的提交记录)

- **回退版本**
>git reset
>git reset --soft(回退到某个版本，保留工作区和暂存区修改的内容)
>git reset --hard(回退到某个版本，丢弃工作区和暂存区修改的内容)
>git reset --mixed(soft和hard之间，回退到某个版本，只保留工作区，丢弃暂存区修改的内容；默认指令)

>复制目录：cp -rf repo repo-soft

>查看历史提交记录，指针指向当前仓库
git log --oneline
e6d5bd1 (HEAD -> master) commit3
4ff2175 commit2
1813b87 commit1
>回退 git reset --soft 4ff2175
>回退到上一个版本 git reset --hard HEAD^

>查看历史操作记录
git reflog

- **git diff**
```
查看工作区、暂存区、本地仓库之间的差异
默认比较工作区和暂存区之间的差异
vi file1.txt(使用vim打开文件，修改之后ESC退出保存)
git diff

git diff HEAD（比较工作区和版本库的差异）
git diff --cached(比较暂存区和版本库的差异)
git diff 4ff2175 1813b87(比较两个指定版本的差异)
git diff HEAD~ HEAD(查看当前版本和上一个版本的差异)
git diff HEAD~2 HEAD file1.txt(查看提交前第二个版本和当前版本，file1.txt文件的差异)
```  

- **git rm**
```
rm file; git add file 先从工作区删除文件，然后在暂存删除内容

git rm file 把文件从工作区和暂存区同时删除;
删除后提交 -> git commit -m'commit'

git rm --cached< file > 把文件从工作区和暂存区同时删除
```
- **.gitignore**
 ```
   忽略不应该加入到版本库中的文件。  
   常见的.gitignore模版 - [GitHub gitignore](https://github.com/github/gitignore)
   ```
   ```
   基本语法:

   # 这是一个注释
    
   # 空行将被忽略
    
   # 忽略特定文件或目录
   /example.txt    # 忽略仓库根目录下的example.txt文件
   logs/           # 忽略所有logs目录
   *.log           # 忽略所有.log文件

   # 忽略所有 .tmp 文件
   *.tmp
   temp?           # 忽略 temp1, temp2 等文件

   # 忽略 build 目录及其内容
   build/

   # 反转忽略规则
   *.log           # 忽略所有 .log 文件
   !important.log  # 但不忽略 important.log 文件

   # 只忽略根目录下的 debug.log 文件
   /debug.log
  ```

  ```
  git add .gitignore
  git commit -m'xxx'
  
  注意：
  .gitignore文件规则从上到下顺序应用，越早定义的规则优先级越高；
  可以在项目的任意目录下创建.gitignore文件，这样只对该目录及其子目录生效
```







