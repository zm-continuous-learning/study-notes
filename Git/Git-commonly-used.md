# Git常用命令
## git init
- 在本地新建一个repo,进入一个项目目录,执行git init,会初始化一个repo,并在当前文件夹下创建一个.git文件夹.
## git clone [URL]/[SSH]
- 获取一个url对应的远程Git repo, 创建一个local copy.  
- clone下来的repo会以url最后一个斜线后面的名称命名,创建一个文件夹,如果想要指定特定的名称,可以git clone [url] newname指定.

## git status
- 查询repo的状态.
- git status -s: -s表示short, -s的输出标记会有两列,第一列是对staging区域而言,第二列是对working目录而言.

## git log
- show commit history of a branch.
- git log branchname可以显示特定分支的log.
- git log --author=[author name] 可以指定作者的提交历史.
- --no-merges可以将merge的commits排除在外.  
- git log --grep 根据commit信息过滤log: git log --grep=keywords   
- git log -S: 加关键字，filter by introduced diff.  
- 比如: git log -SmethodName (注意S和后面的词之间没有等号分隔).  
- git log -p: 显示细节show patch introduced at each commit.  
- 每一个提交都是一个快照(snapshot),Git会把每次提交的diff计算出来,作为一个patch显示给你看.  
- 另一种方法是git show

## git add
- 在提交之前,Git有一个暂存区(staging area),可以放入新添加的文件或者加入新的改动. commit时提交的改动是上一次加入到staging area中的改动,而不是我们disk上的改动.  
- git add .  添加所有改动的文件  
- git add -p 分次添加，每个改动需要确认  

## git diff
- 不加参数的git diff:  
    - show diff of unstaged changes.  
    - 此命令比较的是工作目录中当前文件和暂存区域快照之间的差异,也就是修改之后还没有暂存起来的变化内容.  

- 若要看已经暂存起来的文件和上次提交时的快照之间的差异,可以用:  
    - git diff --cached 命令.只显示一些简单的信息  
    - (Git 1.6.1 及更高版本还允许使用 git diff --staged，效果是相同的).  
- git diff HEAD  
    - show diff of all staged or unstated changes.  
    - 也即比较woking directory和上次提交之间所有的改动.  

- git diff [branchA] [branchB]可以用来比较两个分支.

## git commit
- 提交已经被add进来的改动.  
- git commit -m “the commit message"  
- git commit -a 会先把所有已经track的文件的改动add进来,然后提交(有点像svn的一次提交,不用先暂存). 对于没有track的文件,还是需要git add一下.  
- git commit --amend 增补提交. 会使用与当前提交节点相同的父节点进行一次新的提交,旧的提交将会被取消.(常常被我用来修改上一次提交的messge)  

## git reset
- git reset HEAD:这个命令用来把不小心add进去的文件从staged状态取出来,可以单独针对某一个文件操作: git reset HEAD - - filename, 这个- - 也可以不加.  
- git reset --soft 版本号
  - 作用：用于版本的回退，只进行对commit操作的回退，不影响工作区的文件。
  - 例如：在提交代码的时候，commit之后，然后我又在工作区添加了东西，这时候突然发现，上一次的commit有错误的文件，需要重新修改，但是我添加的东西友不想丢失，而且我想修改上一次的提交，这时候可进行git reset --soft 版本号
- 使用git reset —hard HEAD进行reset,即上次提交之后,所有staged的改动和工作目录的改动都会消失,还原到上次提交的状态.
总结：
- 不带soft和hard参数的git reset,实际上带的是默认参数mixed.  
- git reset --mixed id,是将git的HEAD变了(也就是提交记录变了),但文件并没有改变，(也就是working tree并没有改变). 取消了commit和add的内容.  
- git reset --soft id. 实际上，是git reset –mixed id 后,又做了一次git add.即取消了commit的内容.
- git reset --hard id.是将git的HEAD变了,文件也变了.
- 按改动范围排序如下:
- soft (commit) < mixed (commit + add) < hard (commit + add + local working)

## git stash
- 把当前的改动压入一个栈.
- git stash将会把当前目录和index中的所有改动(但不包括未track的文件)压入一个栈,然后留给你一个clean的工作状态,即处于上一次最新提交处.
- git stash list会显示这个栈的list.
- git stash apply 0 取出stash中的上一个项目(stash@{0}),并且应用于当前的工作目录.
- 也可以指定别的项目,比如git stash apply 1.
- 如果你在应用stash中项目的同时想要删除它,可以用git stash pop
- 删除stash中的项目:
  - git stash drop: 删除上一个,也可指定参数删除指定的一个项目.
  - git stash clear: 删除所有项目.

## git branch
- git branch 列出本地所有分支,当前分支会被星号标示出.
- git branch -v可以看见每一个分支的最后一次提交.
- git branch (branchname)  创建一个新的分支(当你用这种方式创建分支的时候,分支是基于你的上一次提交建立的). 
- git branch -d (branchname)  删除一个分支.
- 删除remote的分支:
- git push (remote-name) :(branch-name)  delete a remote branch.
  - 例：git push origin :test

## git checkout
- git checkout (branchname)   切换到一个分支.
- git checkout -b (branchname): 创建并切换到新的分支.
  - 这个命令是将git branch newbranch和git checkout newbranch合在一起的结果.


## git merge
- 把一个分支merge进当前的分支.
- git merge [alias]/[branch]
  - 把远程分支merge到当前分支.
  - 如果出现冲突,需要手动修改,可以用git mergetool.
  - 解决冲突的时候可以用到git diff,解决完之后用git add添加,即表示冲突已经被resolved.
  - 例子：git merge origin/merge-test

## git remote
- list, add and delete remote repository aliases.
- 因为不需要每次都用完整的url,所以Git为每一个remote repo的url都建立一个别名,然后用git remote来管理这个list.
  - git remote: 列出remote aliases.
  - 如果你clone一个project,Git会自动将原来的url添加进来,别名就叫做:origin.
  - git remote -v:可以看见每一个别名对应的实际url.
  - git remote add [alias] [url]: 添加一个新的remote repo.
  - git remote rm [alias]: 删除一个存在的remote alias.
  - git remote rename [old-alias] [new-alias]: 重命名.
  - git remote set-url [alias] [url]:更新url. 可以加上—push和fetch参数,为同一个别名set不同的存取地址.

## git fetch
- download new branches and data from a remote repository.
- 可以git fetch [alias]取某一个远程repo,也可以git fetch --all取到全部repo
- fetch将会取到所有你本地没有的数据,所有取下来的分支可以被叫做remote branches,它们和本地分支一样(可以看diff,log等,也可以merge到其他分支),但是Git不允许你checkout到它们. 

## git pull
- fetch from a remote repo and try to merge into the current branch.
- pull == fetch + merge FETCH_HEAD
- git pull会首先执行git fetch,然后执行git merge,把取来的分支的head merge到当前分支.这个merge操作会产生一个新的commit.    
- 如果使用git pull --rebase参数,它会执行git rebase来取代原来的git merge，不会产生新的commit。
 
## git rebase
- --rebase不会产生合并的提交,它会将本地的所有提交临时保存为补丁(patch),放在”.git/rebase”目录中,然后将当前分支更新到最新的分支尖端,最后把保存的补丁应用到分支上.
- rebase的过程中,也许会出现冲突,Git会停止rebase并让你解决冲突,在解决完冲突之后,用git add去更新这些内容,然后无需执行commit,只需要:
- git rebase --continue就会继续打余下的补丁.
- git rebase --abort将会终止rebase,当前分支将会回到rebase之前的状态.

## git push
push your new branches and data to a remote repository.
- git push [alias] [branch]
- 将会把当前分支merge到alias上的[branch]分支.如果分支已经存在,将会更新,如果不存在,将会添加这个分支.
- 如果有多个人向同一个remote repo push代码, Git会首先在你试图push的分支上运行git log,检查它的历史中是否能看到server上的branch现在的tip,如果本地历史中不能看到server的tip,说明本地的代码不是最新的,Git会拒绝你的push,让你先fetch,merge,之后再push,这样就保证了所有人的改动都会被考虑进来.

## 特殊符号:
- ^代表父提交,当一个提交有多个父提交时,可以通过在^后面跟上一个数字,表示第几个父提交: ^相当于^1.
- ~<n>相当于连续的<n>个^.

## 杂记
### 因为修改了目录层级导致的代码冲突问题
- 如果本地有commit可以复制到新的分支备份
- 再将主分支的目录层级调整跟修改后的目录层级一样，这样文件才可以顺利比对
- pull下来后，解决代码冲突
- 把复制到新分支的本地提交rebase过来，处理冲突
- 解决后就可以push啦


