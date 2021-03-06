#Learning Git#
---

##1. config
>git config --global  user.name 'xxx' 
git config --global user.email 'xxx@xxx.xx'

config配置git，___--global___ option可以配置全局，保存在～/.gitconfig文件中

##2. init
>cd 'urdir'   
git init

在你的dir下初始化repo。具体初始化的dir和其他路径与dir中的路径的关系，以及使用git命令时的current dir的关系，有待确定。目前看来，可以在dir德尔子目录下使用git，且依然使用dir下的repo。

##3. add/rm&commit
>git add gitnote.rm
git commit -m 'some comment' 
git rm gitnote.rm
git commit -m 'rm'

添加一些文件（***add***），然后提交（***commit***）
***rm***在tempload添加一个删除命令，使用***commit***来提交删除
git rm不但是添加一个删除的命令，且==会和rm命令相同直接删除文件==

##4. status&log
>git status 
git log
git diff

check **workload for _add_** and check the **records of _commit_**
***diff*** shows the differences between the workload and tempload

##5. checkout&reset
>git checkout --gitnote.rm
>git reset --hard HEAD^
>git reset --hard [commitid]

***checkout***将暂存区（如果没有就是最近的分支）的==某个文件==复制到workload，即还原工作区的修改==改变的是workload==
***reset***则会返回版本 注意HEAD的指向，==使用***--hard***参数==

>git reflog

***reflog***返回分支变化记录

***
###sum
some conceptions and commends. 
|workload|------------|tmpload|-----------------|bunch|
  add ------------------>|commit----------------->|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| <---------checkout|<----------------reset

---
##6. github, remote add & push 本地到远程
github 使用ssh验证，关于非对称加密，可见key.rm
>ssh-keygen -t rsa -C ‘myemailadress’ 

使用默认选项，一路回车创建你的密钥。linux在～/.ssh/下有你的公钥和私钥，复制**公钥**到github你的设置中。同时，要新建一个仓库（是否要和本地仓库同名？）
>cd your_repo_dir
>git remote add git@github.com:yournameingithub/yourreponame
>git push -u origin yourbranchname

推送本地到远程需要在仓库目录下，
第一次连接两个仓库要命名一个origin，***push***时-u会把两个仓库的branch关联起来
>git push origin reponame

之后就可以简化推送了
##7. github 远程到本地 clone
>git clone git@github.com:user/repo

任何人都可以clone下来。在pwd，当前路径下创建repo目录。
>git pull

保证本地与远程版本同步
##8.分支--单链条 branch，checkout&merge
>git checkout -b newbranch

该命令等价于以下两个命令
>git branch newbranch
>git checkout newbranch

创建新的分支指针，之后再切换到新的指针
>git branch

可以通过***branch***来查看分支。
在新的分支上进行管理操作，可以不断指向产生一系列新节点
而master（远分支指针）一直会指向当前结点。
但newbranch完成了其使命后，可以直接切回master并合并分支
>git checkout master
git merge newbranch

最后删除newbranch
>git branch -d newbranch

这个newbranch就像个小弟为master在前面探路，保证master的整洁性。
##9. 分支管理
master分支是稳定版本
dev为实际版本，团队合作时，每个人分别在自己的dev分支上工作，完成后提交到一起，注意使用***--no-ff***模式，***这样合并后是在dev上新建一个提交并复制成待合并分支的最新版本，而不是沿着待合并的分支逐个复制***
>git merge --no-ff -m 'no fast forward'

区别：***--no-ff***在***log***中与*fast forward*的记录是相同的
但是在reflog中是不同的：==reflog中的no-ff只会增加指向merged branch的最新提交的记录，而ff会将所有的指针记录复制过来==
##10. stash工作区
>git stash

将工作区的修改保存（剪切）到当前分支下的stash中，这样==切换分支的时候就不会丢失工作区的修改==。可以用于临时转换分支进行修改工作，之后切换回来，读取stash到工作区，继续之前的工作
>git stash list

列出stash的list
>git stash apply
git stash drop

以上两句的功能与下句相同
>git stash pop

对于多个stash 可使用来指定stash回复到工作区
>git stash apply stash@{0}

##11. 推送远程dev分支
>git clone git@github.com:usrname/repo

从远程库克隆
这时默认只有master分支，其他分支没有对应关系
>git checkout -b dev origin/dev

基于远程origin库/dev分支建立本地dev分支，用以***push***
>git branch -set-upstream dev origin/dev

用以***pull***