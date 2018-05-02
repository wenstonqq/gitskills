# gitskills
git 的一些技能

## 常用git命令

### 创建版本库

首先，选择一个合适的地方，创建一个空目录：
$ mkdir learngit
$ cd learngit
$ pwd
pwd命令用于显示当前目录。在我的Mac上，这个仓库位于/Users/qiangqiangwen/learngit。
第二步，通过git init命令把这个目录变成Git可以管理的仓库：
$ git init
Initialized empty Git repository in /Users/qiangqiangwen/learngit/.git/

### 把一个文件放到Git仓库只需要两步。

第一步，用命令git add告诉Git，把文件添加到仓库：
$ git add readme.txt
执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

第二步，用命令git commit告诉Git，把文件提交到仓库：
$ git commit -m "wrote a readme file"
[master (root-commit) cb926e7] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

### Git鼓励大量使用分支：

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>

### 多人协作

- 查看远程库信息，使用git remote -v；

- 本地新建的分支如果不推送到远程，对其他人就是不可见的；

- 从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；

- 在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；

- 建立本地分支和远程分支的关联，使用git branch --set-upstream-to=origin/branch-name；

- 从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。

### 创建标签
- 命令git tag <name>用于新建一个标签，默认为HEAD，也可以指定一个commit id；

- git tag -a <tagname> -m "blablabla..."可以指定标签信息；

- git tag -s <tagname> -m "blablabla..."可以用PGP签名标签；

- 命令git tag可以查看所有标签。

### 操作标签
- 命令git push origin <tagname>可以推送一个本地标签；

- 命令git push origin --tags可以推送全部未推送过的本地标签；

- 命令git tag -d <tagname>可以删除一个本地标签；

- 命令git push origin :refs/tags/<tagname>可以删除一个远程标签。
