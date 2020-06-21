### 一、GIt 工作流程
- 克隆 Git 资源作为工作目录。
- 在克隆的资源上添加或修改文件。
- 如果其他人修改了，你可以更新资源。
- 在提交前查看修改。
- 提交修改。
- 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。
### 二、Git 创建仓库

**1.从当前目录打开 `Git Bash Here` ，输入初始化命令**
```
git init
```
**该命令执行完后会在当前目录生成一个 *.git* 目录。**
**2.指定目录作为Git仓库**
```
git init FileName
```
**该命令执行完后会在当前目录下的 *FileName* 目录下生成一个 *.git* 目录，如果当前目录下没有 *FileName* 目录，则会生成一个空目录**  
### 三、将目录下的文件纳入版本控制
```
$ git add .
$ git add FileName
$ git commit -m '初始化项目版本'
```
### 四、克隆仓库
1.我们使用 `git clone` 从现有 Git 仓库中拷贝项目
```
$ git clone git@github.com:****/***.git
```
2.如果我们需要克隆到指定的目录，可以使用以下命令格式
```
git clone <repo> <directory>
```
3.如果要自己定义要新建的项目目录名称，可以在命令末尾指定新的名字
```
$ git clone git@github.com:****/***.git mygrit
```

### 五、基本快照

**1.`git add`**

该命令将文件添加到缓存
* 添加一个文件时
  * `git add FileName`
* 添加两个文件时
  * ```
    $ touch README
    $ touch hello.php
    $ ls
    README        hello.php
    $ git add README hello.php 
    ```
* 添加所有更改时
  * `git add .`

**2.`git status`**

该命令查看上次提交之后是否有修改，使用命令`git status -s`时，可以获得简短的结果输出

**3.`git diff`**

该命令来查看执行`git status`获得的结果的详细信息
* 尚未缓存的改动： git diff
* 查看已经缓存的改动： git diff cached
* 查看已缓存和未缓存的所有改动: git diff HEAD
* 显示摘要而非整个 diff ： git diff --stat

**4.`git commit`

该命令将缓存区内容添加到仓库中，使用命令`git commit -m`命令可以在命令行中添加提交注释

`git commit -a`命令可以跳过`git add`命令


***
### Warning

**1.当 Git 给电脑添加 *github key* 时出现如下问题**
```
$ ssh git@github.com
warning:Permanently added the RSA host key for IP address '192.30.255.113' to the list of known hosts.
```
**解决办法：**
找到系统 *hosts* 文件，在文件里添加GitHub的IP地址：***192.30.225.113***
**2.提交 Git 仓库时出现如下问题**
```
Your branch is up-to-date with 'origin/master'.
```
**解决办法：**  
* 其根本原因是版本分支的问题，需要新建一个分支，检查是否已经建成
    ```
    $ git branch newbranch
    & git branch
    ```
* 然后切换到分支，将改动提交到新分支
    ```
    $ git add . 
    $ git commit -m "说明"
    ```
* 再切换到主分支，将新分支提交的改动合并到主分支
    ```
    $ git checkout master
    $ git merge newbranch 
    ```
* 然后可以 push 代码了，最后还可以删除分支
    ```
    $ git push -u origin master
    $ git branch -D newbranch
    ```
### Error
**1. Git push 到GitHub的时候遇到**
```
To git@gitee.com:***/****.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@gitee.com:***/****.git'
```
**问题（Non-fast-forward）的出现原因在于：git仓库中已经有一部分代码，所以它不允许你直接把你的代码覆盖上去。**
**解决办法：**  
* 强推。利用强覆盖方式用你本地的代码替代git仓库内的内容，如果远程仓库是刚建的，没有代码，可以这样操作，尽量避免这种操作方法。
    ```
    git push -f
    ```
* 先把 git 的东西 fetch 到你本地然后 merge 后再 push
    ```
    $ git fetch
    $ git merge
    ```

    ```
* 然后输入 git pull , 再执行上传，显示如下
    ```
    $ git pull
    Already up-to-date.
    $ git push origin master
    ```
**2.在 push 更改时遇到如下问题**
```
To git@gitee.com:***/****.git
! [rejected] master -> master (fetch first)
error: failed to push some refs to 'git@gitee.com:***/****.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
**解决办法：**
* 强行让本地分支覆盖远程分支，不建议
    ```
    $ git push origin master -f 
    ```
* pull 把运程分支上的提交合并到本地分支之后再 push
    ```
    $ git pull origin master --allow-unrelated-histories
    ```
### Fatal

**1.在上传本地代码到GitHub仓库时，出现下面这个问题**
```
$ git remote add origin git@github.com:***/****.git
fatal: remote origin already exists.
```
**解决办法：**
先移除
`git remote rm origin`
再次添加
`git remote add origin git@github.com:***/****.git`

**2.在使用 git merge 的时候出现了以下的问题**
```
fatal: refusing to merge unrelated histories
```
**解决办法：**
`git pull origin master --allow-unrelated-histories` 

**3.在使用 git merge 的时候出现了以下的问题**
```
fatal: You have not concluded your merge (MERGE_HEAD exists).
Please, commit your changes before you merge.
```
**解决办法：**
这个是因为我们没有提交当前的变化
```
 git add .
 git commit -am "提交信息"
 git merge
```

