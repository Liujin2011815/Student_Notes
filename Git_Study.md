### һ��GIt ��������
- ��¡ Git ��Դ��Ϊ����Ŀ¼��
- �ڿ�¡����Դ����ӻ��޸��ļ���
- ����������޸��ˣ�����Ը�����Դ��
- ���ύǰ�鿴�޸ġ�
- �ύ�޸ġ�
- ���޸���ɺ�������ִ��󣬿��Գ����ύ���ٴ��޸Ĳ��ύ��
### ����Git �����ֿ�

**1.�ӵ�ǰĿ¼�� `Git Bash Here` �������ʼ������**
```
git init
```
**������ִ�������ڵ�ǰĿ¼����һ�� *.git* Ŀ¼��**
**2.ָ��Ŀ¼��ΪGit�ֿ�**
```
git init FileName
```
**������ִ�������ڵ�ǰĿ¼�µ� *FileName* Ŀ¼������һ�� *.git* Ŀ¼�������ǰĿ¼��û�� *FileName* Ŀ¼���������һ����Ŀ¼**  
### ������Ŀ¼�µ��ļ�����汾����
```
$ git add .
$ git add FileName
$ git commit -m '��ʼ����Ŀ�汾'
```
### �ġ���¡�ֿ�
1.����ʹ�� `git clone` ������ Git �ֿ��п�����Ŀ
```
$ git clone git@github.com:****/***.git
```
2.���������Ҫ��¡��ָ����Ŀ¼������ʹ�����������ʽ
```
git clone <repo> <directory>
```
3.���Ҫ�Լ�����Ҫ�½�����ĿĿ¼���ƣ�����������ĩβָ���µ�����
```
$ git clone git@github.com:****/***.git mygrit
```

### �塢��������

**1.`git add`**

������ļ���ӵ�����
* ���һ���ļ�ʱ
  * `git add FileName`
* ��������ļ�ʱ
  * ```
    $ touch README
    $ touch hello.php
    $ ls
    README        hello.php
    $ git add README hello.php 
    ```
* ������и���ʱ
  * `git add .`

**2.`git status`**

������鿴�ϴ��ύ֮���Ƿ����޸ģ�ʹ������`git status -s`ʱ�����Ի�ü�̵Ľ�����

**3.`git diff`**

���������鿴ִ��`git status`��õĽ������ϸ��Ϣ
* ��δ����ĸĶ��� git diff
* �鿴�Ѿ�����ĸĶ��� git diff cached
* �鿴�ѻ����δ��������иĶ�: git diff HEAD
* ��ʾժҪ�������� diff �� git diff --stat

**4.`git commit`**

�����������������ӵ��ֿ��У�ʹ������`git commit -m`���������������������ύע��

`git commit -a`�����������`git add`����

**5.`git reset HEAD`**

����������ȡ��֮ǰ git add ��ӵĻ��棬�÷����ں�������ļ���

**6.`git mv`**

�����������ƶ���������һ���ļ���Ŀ¼��������

```
$ git mv README  README.md
$ ls
README.md
```

**7.`git rm`**

* ���ֻ�Ǽ򵥵شӹ���Ŀ¼���ֹ�ɾ���ļ������� git status ʱ�ͻ��� `Changes not staged for commit `����ʾ��Ҫ�� Git ���Ƴ�ĳ���ļ�����* ����Ҫ���Ѹ����ļ��嵥���Ƴ���Ȼ���ύ������������������ɴ����
`git rm <file>`
* ���ɾ��֮ǰ�޸Ĺ������Ѿ��ŵ��ݴ�����Ļ��������Ҫ��ǿ��ɾ��ѡ�� -f
`git rm -f <file>`
* ������ļ����ݴ������Ƴ�������Ȼϣ�������ڵ�ǰ����Ŀ¼�У����仰˵�����ǴӸ����嵥��ɾ����ʹ�� --cached ѡ���
`git rm --cached <file>`
* ������ɾ�� hello.php�ļ���
    ```
    $ git rm hello.php 
    rm 'hello.php'
    $ ls
    README
    ```
* ���ӹ�������ɾ���ļ���
    ```
    $ git rm --cached README 
    rm 'README'
    $ ls
    README
    ```
* ���Եݹ�ɾ������������������һ��Ŀ¼��Ϊ���������ݹ�ɾ������Ŀ¼�е�������Ŀ¼���ļ�;����ĳ��Ŀ¼�У�ִ�д���䣬��ɾ����Ŀ¼�µ������ļ�����Ŀ¼
`git rm �Cr * `

### ������֧����

������֧���`git branch (branchname)`

�л���֧����:`git checkout (branchname)`

�ϲ���֧����:`git merge `

�г���֧���`git branch`

�����·�֧�������л����÷�֧��`git checkout -b (branchname)`

ɾ����֧���`git branch -d (branchname)`

### �ߡ�Git �鿴�ύ��ʷ

���`git log`

�鿴��ʷ��¼�ļ��汾���`git log --oneline`

�鿴��֧�ͺϲ�����ʷ���`git log --graph`

������`--reverse`ѡ����������ʾ������־�����磺
```
$ git log --reverse --oneline
3b58100 ��һ�ΰ汾�ύ
3e92c19 add test.txt
c1501a2 removed test.txt��add runoob.php
7774248 (change_site) changed the runoob.php
c68142b �޸Ĵ���
d5e9fc2 (HEAD -> master) Merge branch 'change_site'
```

����ָ���û����ύ��־���`git log --author`,���磺
```
$ git log --author=Linus --oneline -5
81b50f3 Move 'builtin-*' into a 'builtin/' subdirectory
3bb7256 make "index-pack" a built-in
377d027 make "git pack-redundant" a built-in
b532581 make "git unpack-file" a built-in
112dd51 make "mktag" a built-in
```

ָ�����ڲ鿴(����`--no-merges`ѡ�������غϲ��ύ)��
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

### �ˡ�Git ��ǩ

���`git tag ��ǩ��Ϣ`

���� `-a` ѡ��������һ����ע��ı�ǩ������
```
$ git tag -a v1.0
```
ִ�д�����ʱ��Git �����ı༭��������дһ���ǩע��

�鿴���б�ǩ���`git tag`

### �š�Git Զ�ֿ̲⣨Github��

**���زֿ�����Զ�ֿ̲�**
���� SSH Key ���`$ ssh-keygen -t rsa -C "youremail@example.com"`
* ����� your_email@youremail.com ��Ϊ���� Github ��ע������䣬֮���Ҫ��ȷ��·�����������룬������ʹ��Ĭ�ϵ�һ·�س����С��ɹ��Ļ����� ~/ ������ .ssh �ļ��У���ȥ���� id_rsa.pub����������� key��
* �ص� github �ϣ����� Account => Settings���˻����ã���
* ���ѡ�� SSH and GPG keys��Ȼ���� New SSH key ��ť,
* title ���ñ��⣬��������ճ��������������ɵ� key��

**�鿴��ǰ�˻�Զ�ֿ̲�����**��`git remote`

**��ȡԶ�ֿ̲����**
��ȡԶ�ֿ̲����`git fetch` 
�ϲ�����ǰ��֧���`git merge`
* ���������ú���һ��Զ�ֿ̲⣬��������Ҫ��ȡ���µ����ݣ����������ִ�� git fetch [alias] ���� Git ȥ��ȡ������û�е����ݣ�Ȼ�������ִ�� git merge [alias]/[branch] �Խ��������ϵ��κθ��£�����������ʱ�����͵��������ˣ��ϲ�����ĵ�ǰ��֧��

**���͵�Զ�ֿ̲�**
��������·�֧�����ݵ�ĳ��Զ�˲ֿ�����:
`git push [alias] [branch]`
���������� [branch] ��֧���ͳ�Ϊ [alias] Զ�ֿ̲��ϵ� [branch] ��֧��ʵ�����¡�
```
$ touch runoob-test.txt      # ����ļ�
$ git add runoob-test.txt 
$ git commit -m "��ӵ�Զ��"
master 69e702d] ��ӵ�Զ��
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 runoob-test.txt

$ git push origin master    # ���͵� Github
```

**���Զ�ֿ̲�**
`git remote add [shortname] [url]`

**ɾ��Զ�ֿ̲�**
`git remote rm [����]`

```
$ git remote -v
origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin    git@github.com:tianqixin/runoob-git-test.git (push)

# ��Ӳֿ� origin2
$ git remote add origin2 git@github.com:tianqixin/runoob-git-test.git

$ git remote -v
origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin    git@github.com:tianqixin/runoob-git-test.git (push)
origin2    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin2    git@github.com:tianqixin/runoob-git-test.git (push)

# ɾ���ֿ� origin2
$ git remote rm origin2
$ git remote -v
origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
origin    git@github.com:tianqixin/runoob-git-test.git (push)
```






***
### Warning

**1.�� Git ��������� *github key* ʱ������������**
```
$ ssh git@github.com
warning:Permanently added the RSA host key for IP address '192.30.255.113' to the list of known hosts.
```
**����취��**
�ҵ�ϵͳ *hosts* �ļ������ļ������GitHub��IP��ַ��***192.30.225.113***
**2.�ύ Git �ֿ�ʱ������������**
```
Your branch is up-to-date with 'origin/master'.
```
**����취��**  
* �����ԭ���ǰ汾��֧�����⣬��Ҫ�½�һ����֧������Ƿ��Ѿ�����
    ```
    $ git branch newbranch
    & git branch
    ```
* Ȼ���л�����֧�����Ķ��ύ���·�֧
    ```
    $ git add . 
    $ git commit -m "˵��"
    ```
* ���л�������֧�����·�֧�ύ�ĸĶ��ϲ�������֧
    ```
    $ git checkout master
    $ git merge newbranch 
    ```
* Ȼ����� push �����ˣ���󻹿���ɾ����֧
    ```
    $ git push -u origin master
    $ git branch -D newbranch
    ```
### Error
**1. Git push ��GitHub��ʱ������**
```
To git@gitee.com:***/****.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@gitee.com:***/****.git'
```
**���⣨Non-fast-forward���ĳ���ԭ�����ڣ�git�ֿ����Ѿ���һ���ִ��룬��������������ֱ�Ӱ���Ĵ��븲����ȥ��**
**����취��**  
* ǿ�ơ�����ǿ���Ƿ�ʽ���㱾�صĴ������git�ֿ��ڵ����ݣ����Զ�ֿ̲��Ǹս��ģ�û�д��룬�������������������������ֲ���������
    ```
    git push -f
    ```
* �Ȱ� git �Ķ��� fetch ���㱾��Ȼ�� merge ���� push
    ```
    $ git fetch
    $ git merge
    ```

    ```
* Ȼ������ git pull , ��ִ���ϴ�����ʾ����
    ```
    $ git pull
    Already up-to-date.
    $ git push origin master
    ```
**2.�� push ����ʱ������������**
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
**����취��**
* ǿ���ñ��ط�֧����Զ�̷�֧��������
    ```
    $ git push origin master -f 
    ```
* pull ���˳̷�֧�ϵ��ύ�ϲ������ط�֧֮���� push
    ```
    $ git pull origin master --allow-unrelated-histories
    ```
### Fatal

**1.���ϴ����ش��뵽GitHub�ֿ�ʱ�����������������**
```
$ git remote add origin git@github.com:***/****.git
fatal: remote origin already exists.
```
**����취��**
���Ƴ�
`git remote rm origin`
�ٴ����
`git remote add origin git@github.com:***/****.git`

**2.��ʹ�� git merge ��ʱ����������µ�����**
```
fatal: refusing to merge unrelated histories
```
**����취��**
`git pull origin master --allow-unrelated-histories` 

**3.��ʹ�� git merge ��ʱ����������µ�����**
```
fatal: You have not concluded your merge (MERGE_HEAD exists).
Please, commit your changes before you merge.
```
**����취��**
�������Ϊ����û���ύ��ǰ�ı仯
```
 git add .
 git commit -am "�ύ��Ϣ"
 git merge
```

