设置用户名称：$ git config --global user.name  *"Your Name"*  
设置用户邮箱：$ git config --global user.email *"email@example.com"*  
# 创建版本库  
1.创建空目录：$ mkdir *"address"*  
2.切换至该目录: $ cd *"address"*  
3.建立仓库： 4 git init  
# 添加文件
1.添加 ：$ git add *"your file"*  
2. 提交 :$ git commit -m *"explains"*  

查看仓库状态: $ git status  
查看文件修改情况: $ git diff *"your file"*  
查看文件提交记录: $ git log  或者: $ git log pretty=online  

git中***head***表示当前版本，上个版本***head^***,上上个***head^^***，上n个***head~n***  
本地仓库返回上一版本: $ git reset -hard HEAD^ ,HEAD^可替换为 commit id  
查看每一次命令: $ git reflog  
## 工作区  
就是你在电脑里能看到的目录，比如电脑中的仓库文件夹就是一个工作区  
工作区就是你存放一切文件的那个目录。比如前面我们新建了一个目录，叫test，然后进入test，在test目录下使用git init命令把test变成了一个Git可以管理的目录。我们甚至还知道Git帮我们自动生成了一个隐藏目录叫.git。此时，这个test目录就是工作区。
## 版本库  
工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。  
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git自动创建的第一个分支master，以及指向master的一个指针叫HEAD。  
## 暂存区  
这个index文件就是暂存区（stage）。
事实上，暂存区是版本库里的一个临时存储的地方，经由暂存区，再提交到版本库。
>1.首先，你在工作区创建了一个文件或者修改了一个文件  
2.然后你有输入了git add，此时文件实际上是被添加到了暂存区（stage），也就是那个index文件  
3.接着，你又输入git commit，这才算是正式提交。Git默认给我们创建了一个master分支（以后会详说）和一个指向master分支的HEAD指针（就是上面的HEAD文件）。  

# 管理修改
撤销文件在工作区的修改，返回至版本库或暂存区: $ git checkout --***your file***  
若只提交至暂存区: $ git reset HEAD ***your file***  
直接删除文件: $ rm ***your file***,删除版本库: $ git rm ***your file***,再git commit -m"....."  
从版本库恢复文件至工作区: git checkout -- ***your file***    
# github  
关联GitHub仓库: $ git remote add origin *.......*   
将本地master推送至远程master并相关联: $ git push -u origin master  
将本地推送至远程: $ git push origin master  
克隆远程库: $ git clone *.......*  
创建并切换至*dev*分支: $ git checkout -b *dev* 相当于: $ git branch *dev* $ git checkout *dev*  
合并分支: 先切换至master，然后: $ git merge *dev*  
删除分支: $ git branch -d *branchname*  
本地分支有冲突无法快速合并时需手动解决冲突  
普通模式合并: $ git merge --no-ff -m"*......*" *branch name*  
暂存工作区: $ git stash  
恢复工作区并删除stash内容: $ git stash pop  
恢复工作区但不删除stash内容: $ git stash apply  
删除stash内容: $ git stash drop  
丢弃一个未合并的分支: $ git branch -D *branch name*  
创建远程origin的dev分支到本地: $ git checkout -b *branchname* origin/*origin branch name*  
上传分支到远程: $ git push origin/*branch name*  
制定本地dev分支与远程dev分支: $ git branch --set-upstream-to=*origin/dev* dev  

