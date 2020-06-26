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

**4.`git commit`**

该命令将缓存区内容添加到仓库中，使用命令`git commit -m`命令可以在命令行中添加提交注释

`git commit -a`命令可以跳过`git add`命令

**5.`git reset HEAD`**

该命令用来取消之前 git add 添加的缓存，用法是在后面加上文件名

**6.`git mv`**

该命令用于移动或重命名一个文件、目录、软连接

```
$ git mv README  README.md
$ ls
README.md
```

**7.`git rm`**

* 如果只是简单地从工作目录中手工删除文件，运行 git status 时就会在 `Changes not staged for commit `的提示。要从 Git 中移除某个文件，就* 必须要从已跟踪文件清单中移除，然后提交。可以用以下命令完成此项工作
`git rm <file>`
* 如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f
`git rm -f <file>`
* 如果把文件从暂存区域移除，但仍然希望保留在当前工作目录中，换句话说，仅是从跟踪清单中删除，使用 --cached 选项即可
`git rm --cached <file>`
* 如我们删除 hello.php文件：
    ```
    $ git rm hello.php 
    rm 'hello.php'
    $ ls
    README
    ```
* 不从工作区中删除文件：
    ```
    $ git rm --cached README 
    rm 'README'
    $ ls
    README
    ```
* 可以递归删除，即如果后面跟的是一个目录做为参数，则会递归删除整个目录中的所有子目录和文件;进入某个目录中，执行此语句，会删除该目录下的所有文件和子目录
`git rm –r * `

### 六、分支管理

创建分支命令：`git branch (branchname)`

切换分支命令:`git checkout (branchname)`

合并分支命令:`git merge `

列出分支命令：`git branch`

创建新分支并立即切换到该分支：`git checkout -b (branchname)`

删除分支命令：`git branch -d (branchname)`

### 七、Git 查看提交历史

命令：`git log`

查看历史记录的简洁版本命令：`git log --oneline`

查看分支和合并的历史命令：`git log --graph`

可以用`--reverse`选项来逆向显示所有日志，比如：
```
$ git log --reverse --oneline
3b58100 第一次版本提交
3e92c19 add test.txt
c1501a2 removed test.txt、add runoob.php
7774248 (change_site) changed the runoob.php
c68142b 修改代码
d5e9fc2 (HEAD -> master) Merge branch 'change_site'
```

查找指定用户的提交日志命令：`git log --author`,比如：
```
$ git log --author=Linus --oneline -5
81b50f3 Move 'builtin-*' into a 'builtin/' subdirectory
3bb7256 make "index-pack" a built-in
377d027 make "git pack-redundant" a built-in
b532581 make "git unpack-file" a built-in
112dd51 make "mktag" a built-in
```

指定日期查看(其中`--no-merges`选项是隐藏合并提交)：
```
$ git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges
5469e2d Git 1.7.1-rc2
d43427d Documentation/remote-helpers: Fix typos and improve language
272a36b Fixup: Second argument may be any arbitrary string
b6c8d2d Documentation/remote-helpers: Add invocation section
5ce4f4e Documentation/urls: Rewrite to accomodate transport::address
00b84e9 Documentation/remote-helpers: Rewrite description
03aa87e Documentation: Describe other situations where -z affects git diff
77bc694 rebase-interactive: silence warning when no commits rewritten
636db2c t3301: add tests to use --format="%N"
```

### 八、Git 标签

命令：`git tag 标签信息`

带上 `-a` 选项来创建一个带注解的标签，例如
```
$ git tag -a v1.0
```
执行此命令时，Git 会打开你的编辑器，让你写一句标签注解

查看所有标签命令：`git tag`

### 九、Git 远程仓库（Github）

**本地仓库连接远程仓库**
生成 SSH Key 命令：`$ ssh-keygen -t rsa -C "youremail@example.com"`
* 后面的 your_email@youremail.com 改为你在 Github 上注册的邮箱，之后会要求确认路径和输入密码，我们这使用默认的一路回车就行。成功的话会在 ~/ 下生成 .ssh 文件夹，进去，打开 id_rsa.pub，复制里面的 key。
* 回到 github 上，进入 Account => Settings（账户配置）。
* 左边选择 SSH and GPG keys，然后点击 New SSH key 按钮,
* title 设置标题，可以随便填，粘贴在你电脑上生成的 key。

**查看当前账户远程仓库命令**：`git remote`

**提取远程仓库更新**
提取远程仓库命令：`git fetch` 
合并到当前分支命令：`git merge`
* 假设你配置好了一个远程仓库，并且你想要提取更新的数据，你可以首先执行 git fetch [alias] 告诉 Git 去获取它有你没有的数据，然后你可以执行 git merge [alias]/[branch] 以将服务器上的任何更新（假设有人这时候推送到服务器了）合并到你的当前分支。

**推送到远程仓库**
推送你的新分支与数据到某个远端仓库命令:
`git push [alias] [branch]`
以上命令将你的 [branch] 分支推送成为 [alias] 远程仓库上的 [branch] 分支，实例如下。
```
$ touch runoob-test.txt      # 添加文件
$ git add runoob-test.txt 
$ git commit -m "添加到远程"
master 69e702d] 添加到远程
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 runoob-test.txt

$ git push origin master    # 推送到 Github
```

**添加远程仓库**
`git remote add [shortname] [url]`

**删除远程仓库**
`git remote rm [别名]`

```
$ git remote -v
origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin    git@github.com:tianqixin/runoob-git-test.git (push)

# 添加仓库 origin2
$ git remote add origin2 git@github.com:tianqixin/runoob-git-test.git

$ git remote -v
origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin    git@github.com:tianqixin/runoob-git-test.git (push)
origin2    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin2    git@github.com:tianqixin/runoob-git-test.git (push)

# 删除仓库 origin2
$ git remote rm origin2
$ git remote -v
origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin    git@github.com:tianqixin/runoob-git-test.git (push)
```






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

