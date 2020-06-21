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

**4.`git commit`

�����������������ӵ��ֿ��У�ʹ������`git commit -m`���������������������ύע��

`git commit -a`�����������`git add`����


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

