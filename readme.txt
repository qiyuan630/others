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