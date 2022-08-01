### 命令主要有：

1.clone

2.checkout

3.add

4.commit

5.fetch

6.pull

7.push

### 设置用户信息

```
git config --global user.name "your_user_name"
git config --global user.email "email_name@email.com"
```

```
ls -al    # 用于输出当前目录所有文件及其基本信息
```

### 常用命令

在指定文件夹空白处，右键，Git Bash Here

`git init`  初始化当前目录为一个git仓库

1.`git add` .(工作区 --> 暂存区) git add .添加所有文件、文件夹和子文件夹，包括.gitignore和以点开头的任何其他内容；

2.`git commit` (暂存区 --> 本地仓库)，一般形式为git commit -m ‘注释内容’

3.`git status` 查看修改的状态

4.查看提交日志

`git log`

`git log --pretty=oneline`

`git log --pretty=oneline --abbrev-commit`

`git log --pretty=oneline --abbrev-commit --all`

`git log --pretty=oneline --abbrev-commit --all --graph`

5.版本回退

`git reset --hard commitID`

`git reflog` 用于查看已经删除的提交记录

6.添加文件至忽略列表

`touch .gitignore` 生成.ignore文件

vi 编辑，insert 键，Esc到页尾，输入冒号：wq.

7.`git branch` 查看本地分支

8.`git branch branch _name` 创建本地分支

9.`git checkout branch_name` 切换分支，`git checkout -b branch_name` 创建并切换分支

10.`git merge branch_name` 合并分支

分支上的内容必须先提交，才能切换分支，master是主线，一般将分支合并到主线上面。

步骤：切换到master分支，然后执行合并命令，执行完后，分支上的资源、文件就会被合并到主线上。

11.删除分支

不能删除当前分支，只能删除其他分支。

`git branch -d branch_name` 删除分支时，需要做各种检查

`git branch -D branch_name` 不做任何检查，强制删除

12.解决冲突

直接手动删除文件中的一个分支，留下一个分支，这样就不会有冲突了。

步骤：1.处理文件冲突的地方。

2.将解决完冲突的文件加入暂存区。

3.提交到仓库。

### 远程仓库

先不要添加一个新的远程仓库。

配置SSH公钥

`ssh-keygen -t rsa -C "email_name@email.com"` 生成SSH公钥，不断回车，如果公钥已经存在，则自动覆盖。

`cat ~/.ssh/id_rsa.pub` 获取公钥

文件id_rsa.pub路径C:\Users\Administrator\.ssh，也可以手动复制，将SSH公钥添加到github的Settings->SSH and GPG Keys

`ssh -T git@github.com` 验证是否配置成功

`git remote add origin 仓库路径ssh` 添加远程仓库

`git remote` 查看远程仓库

命令：`git push [-f] [–set-upstream] [远端名称 [本地分支名][:远端分支名] ]`

如果远程分支名和本地分支名称相同，则可以只写本地分支

本来是：`git push origin master ：master` 表示将本地仓库的master分支提交到远程仓库的master分支

`git push origin master` 这里表示将本地仓库当前master分支的内容推到远程仓库上面去

-f 表示强制覆盖

–set-upstream 推送到远端的同时并且建立起和远端分支的关联关系。

`git push --set-upstream origin master`

如果**当前分支已经和远端分支关联**，则可以省略分支名和远端名。

查看关联关系我们可以使用 `git branch -vv` 命令

如果已经有一个远端仓库，我们可以直接clone到本地。

命令: `git clone <仓库路径> [本地目录]`本地目录可以省略，会自动生成一个目录，就是SSH后面那部分

抓取 命令：`git fetch [remote name] [branch name]`

**抓取指令就是将仓库里的更新都抓取到本地，不会进行合并**，不合并本地仓库就是没有更新，此时还没有拿到远程仓库的内容，合并后才会拿到更新的内容。

如果不指定远端名称和分支名，则抓取所有分支。

拉取 命令：`git pull [remote name] [branch name]`

**拉取指令就是将远端仓库的修改拉到本地并自动进行合并，等同于fetch+merge**

如果不指定远端名称和分支名，则抓取所有并更新当前分支。

只去执行抓取命令 `git fetch`，本地仓库是没有远程仓库来的内容的