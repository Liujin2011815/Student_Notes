### 一、Git 创建仓库

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
### 二、




***
### Warning

**1.当 Git 给电脑添加 *github key* 时出现如下问题**
```
$ ssh git@github.com
warning:Permanently added the RSA host key for IP address '192.30.255.113' to the list of known hosts.
```
**解决办法：**
找到系统 *hosts* 文件，在文件里添加GitHub的IP地址：***192.30.225.113***
**2.**

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

