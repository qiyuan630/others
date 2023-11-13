readme.txt
Git is a distributed version control system
Git is free software

更改git的姓名邮箱
git config --global user.name
git config --global user.gamil

添加仓库
git init

添加文件
git add 文件

查看当前文件状态
git status

提交文件
git commit -m""

列出文件更改的情况
git log
git log --pretty=oneline

版本回退
git reset --hard HEAD^ 
这里一个^代表上面一步，几个^就代表往前推多少步骤
这里的回退是直接回去了，之前对文件进行的操作步骤都将抹除就像时光机一样

展示文件
cat 文件（这里要添加文件的.txt）

如果之前的命令提示符情况没有删除的话
我们可以根据版本号返回
git reset --hard 版本号

现在，你回退到了某个版本，关掉了电脑，
第二天早上就后悔了，想恢复到新版本怎么办？找不到新版本的commit id怎么办？
在Git中，总是有后悔药可以吃的。当你用$ git reset --hard HEAD^回退到add distributed版本时，
再想恢复到append GPL，就必须找到append GPL的commit id。Git提供了一个命令git reflog用来记录你的每一次命令：

第一次修改 -> git add -> 第二次修改 -> git commit
你看，我们前面讲了，Git管理的是修改，当你用git add命令后，在工作区的第一次修改被放入暂存区，
准备提交，但是，在工作区的第二次修改并没有放入暂存区，所以，git commit只负责把暂存区的修改提交了，
也就是第一次的修改被提交了，第二次的修改不会被提交。

廖雪峰讲到的是 git checkout --filename 来丢弃工作区的内容
但新版本的git语法是 git restore filename

如果上传到暂存区，我们可以使用git restore --staged filename

git rm filename 这是一种直接删除文件的方式，如果删除之后直接commit那么就是直接删除了，如果没有commit，那么我们可以restore

添加远程仓库地址git remote add origin git
更改远程仓库的地址git remote set-url origin 新地址

完成链接git push origin master
查看远程库链接git remote -v
删除远程库 git remote rm origin 
这一部分结束了


在使用git clone 远程仓库时，要注意首先要完成密钥链接，就是远端和本地密钥链接。ssh-keygen -t rsa -C"2050157259@qq.com"
用ssh -T git@gitee.com这个来确认是否链接成功
远程克隆代码git clone git@github.com:michaelliao/gitskills.git

git checkout -b dev  这里的效果和git switch -c dev是相同的
与以下代码效果相同
git branch dev
git checkout dev    
这里可以进行正常的添加和提交工作。

完成了dev分支下的更改之后，可以转换到master分支

可以将dev分支合并到master分支上：
git merge dev

删除dev分支 git branch -d dev

准备新的feature1分支，继续我们的新分支开发：
git switch -c featurel
git add readme.txt
切换到master分支
git switch master

删除featurel分支：git branch -d featurel

新建并切换分支到git switch -c dev
git merge --no-ff -m""分支     这个是用来禁用fast forward

git stash  可以将当前状态的工作区和暂存区都存储起来
git stash apply 可以恢复状态，git stash drop删除状态。
git stash pop 回复状态并且把stash 的内容删除

git ls-files --with-tree=HEAD这个命令可以看当前状态下的文件夹及文件夹名称
预览要删除的文件夹文件git rm -r -n --cached 文件/文件夹名称
删除文件夹git rm -r --cached 文件/文件夹名称

现在，你的小伙伴要在dev分支上开发，就必须创建远程origin的dev分支到本地，于是他用这个命令创建本地dev分支：
git checkout -b dev origin/dev


现在我们对这一部分学习告一段落已经足够我们使用了
我们学习到https://www.liaoxuefeng.com/wiki/896043488029600/900375748016320中的多人协作部分
由于我们还停留在个人使用层面，故到这里告一段落