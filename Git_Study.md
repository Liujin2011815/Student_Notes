### һ��Git �����ֿ�

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
### ����




***
### Warning

**1.�� Git ��������� *github key* ʱ������������**
```
$ ssh git@github.com
warning:Permanently added the RSA host key for IP address '192.30.255.113' to the list of known hosts.
```
**����취��**
�ҵ�ϵͳ *hosts* �ļ������ļ������GitHub��IP��ַ��***192.30.225.113***
**2.**

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

