# 1、简介
- git是目前世界上最先进的分布式版本控制系统
- 版本控制
> !\[之前](./aa.png)<br>
> !\[现在](./bb.png)
- 诞生
> Linus在1991年创建了开源的Linux<br>
> cvs和svn是集中式的版本控制系统，不但网速慢而且必须联网才能使用。<br>
> 2002年免费使用BitKeeper,直到2005年开发Samba的Andrew试图破解BitKeeper的协议，被BitMover公司发现，收回了免费使用权
> linus花了两周的时间自己用C写了分布式版本控制系统
- 集中式vs分布式
> 集中式版本控制系统是集中存放在中央服务器的，使用时要先从中央服务器取得最新的版本，然后进行编码，再把自己的代码推送给中央服务器。最大的问题就是必须联网才能工作。
> 分布式版本控制系统没有中央服务器，每个人的电脑都是一个完整的版本库，这样工作的时候就不需要网络了。安全性较高，还有强大的分支管理。
- 安装git
> git的包msysgit下载地址：https://git-for-windows.github.io<br>
> 安装后在开始菜单里找到git>git bash 弹出一个命令框，在里面输入
>> $ git config --global user.name "Your Name"<br>
$ git config --global user.email "email@example.com"
- 创建版本库
> windows系统，确保目录名不包含中文
> 通过git init 命令可以把目录变成git可以管理的仓库，会在目录下多.git的目录，这个目录就是git跟踪管理版本库的，不要手动修改这个目录里的文件，不然git仓库就被破坏了
# 2、时光机穿梭
- 修改文件并上传
> $git status 查看仓库的状态<br>
> $git diff 查看不同<br>
> $git add  提交修改，把文件添加进去，实际上就是把文件修改添加到暂存区<br>
> $git status 显示将要被提交的修改文件<br>
> $git commit -m "" 提交更改，实际上就是把暂存区的所有内容提交到当前分支
- 版本回退
> $git log 显示从最近到最远的提交日志<br>
> $git log --pretty=oneline 显示简洁版提交日志<br>
> $git reset --hard head^ 回退到上一版本<br>
> $git reset -- hard head~100 回退到100个版本前<br>
> $cat 文件名  查看文件内容<br>
> $git log 已经没有最新版本的日志了<br>
> $git reset --hard 日志id  返回到最新版本<br>
> 如果不知道commit id但是想恢复到最新版本<br>
> $git reflog 记录每一次命令，会显示每次提交的commit id
- 工作区和暂存区
> 工作区就是电脑里能看到的目录
> 版本库就是文件夹下的.git，版本库里有很多东西，最重要的就是称为stage的暂存区，还有git自动创建的第一个分支master,以及影响master的一个指针叫head。<br>
> !\[图示](./dd.png)<br>
> !\[图示](./ee.png)
- 管理修改
> git跟踪并管理的是修改而非文件。
- 撤销修改
> $git checkout -- readme.txt 把文件在工作区的修改全部撤销，让这个文件回到最近一次git commit或git add时的状态。<br>
> $git reset head file 可以把暂存区的修改撤销掉（unstage），重新放回工作区,然后再撤销工作区
- 删除文件
> $ rm test.txt  直接在文件管理器中把没用的文件删了，Git知道你删除了文件，因此，工作区和版本库就不一致了，git status命令会立刻告诉你哪些文件被删除了<br>
> $git rm test.txt  确实要从版本库中删除该文件 并且 git commit  文件已经在版本库中删除了<br>
> $git checkout -- test.txt 把误删的文件恢复到最新版本
# 3、远程仓库
> 查看是否已经有ssh秘钥 cd ~/.ssh<br>
> $ ssh-keygen -t rsa -C “873082926@qq.com”  生成秘钥<br>
> .ssh文件中得到了两个文件：id_rsa和id_rsa.pub，其中id_rsa.pub就是我们要使用的那个复制里面的全部内容，粘贴到github获取自己的git服务器ssh_key指定位置.<br>
- 添加远程库
> 本地创建一个git仓库，又想在github创建一个git仓库，并且将这两个仓库进行远程同步。<br>

> 1、登陆github，然后在右上角找到create a new repo,创建一个新的仓库。<br>
> 2、在本地仓库下运行命令：
>> $git remote add origin git@github.com:qumeiyu/learngit.git<br>

>3、把本地库上的东西推送上去
>> $git push -u origin master

> 4、今后再推送就可以直接用 $git push origin master<br>
> 注意：第一次使用git的clone或push命令会有一个警告。第一次验证github服务的key时，需要确认github的key的指纹信息，输入yes回车即可。
- 从远程库克隆
> 先创建一个远程库，然后从远程库克隆

> 1、登录github，创建一个新的仓库，勾选initialize this repository with a readme,这样github会自动创建一个readme.md文件。<br>
> 2、在本地命令
>> $git clone https://github.com/qumeiyu/8club.git
# 4、分支管理
> 你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。
- 创建与合并分支
>主分支 master<br>
> 1、创建dev分支，然后切换到dev分支：
>> $ git checkout -b dev<br>
>> 相当于$ git branch dev 和 $git checkout dev 两条命令

> 2、用 $git branch命令查看当前分支
>> git branch命令会列出所有分支，当前分支前面会标一个*

> 3、然后就可以正常提交到分支dev上<br>
> 4、切换回master分支 $git checkout master<br>
> 5、把dev分支合并到master分支上 $git merge dev
>> git merge命令是合并指定分支到当前分支

> 6、合并后 删除dev分支 $git branch -d dev<br>
> 7、查看branch中的分支 $git branch<br>
> 8、总结：
>> 查看分支：git branch  <br>
   创建分支：git branch <name>  <br>
   切换分支：git checkout <name>  <br>
   创建+切换分支：git checkout -b <name>  <br>
   合并某分支到当前分支：git merge <name>  <br>
   删除分支：git branch -d <name>  <br>
- 5、解决冲突
> 1、创建一个新的分支
>> $git checkout -b featurel

> 2、在featurel分支上提交
>> $git add readme.txt <br>
   $git commit -m "and simple"

> 3、切换到master分支、会自动提示当前master分支比远程的master分支要超前1个提交
>> $git checkout master

> 4、在master分支上把readme.txt文件的最后一行改了并提交，现在master分支和featurel分支各自都分别有新的提交。<br>
> 5、这种情况下，Git无法执行“快速合并”，只能试图把各自的修改合并起来，但这种合并就可能会有冲突
>> $ git merge feature1 <br>
    Auto-merging readme.txt<br>
    CONFLICT (content): Merge conflict in readme.txt<br>
    Automatic merge failed; fix conflicts and then commit the result.

> 6、git status 查看冲突文件，修改文件后再提交<br>
> 7、git log可以看到分支合并情况<br>
> 8、删除featurel分支<br>
> 9、$git log --graph 命令可以查看分支合并图
- 分支管理策略
> 合并分支时，git会用fast forword模式，删除分支后，会丢掉分支信息。下面实现--no-ff方式的git merge<br>
> 1、创建并切换dev分支<br>
> 2、修改文件并提交一个新的commit<br>
> 3、切换回到master分支<br>
> 4、合并dev分支，注意--no-ff参数表示禁用fast forward
>> $git merge --no-ff -m "merge with no-ff" dev

> 5、查看分支历史
>> $ git log --graph --pretty=oneline --abbrev-commit

> 6、分支策略基本原则
>> 首先，master分支应该是非常稳定的，也就是说仅用来发布版本，平时不能在上面干活；<br>
   应该在dev分支上干活，到一定的时候，比如说版本发布时再把dev分支g合并到master上。<br>
   合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。
- bug分支
> 当你接到一个修复一个代号101的bug的任务时，很自然地，你想创建一个分支issue-101来修复它，但是，等等，当前正在dev上进行的工作还没有提交<br>
> 并不是你不想提交，而是工作只进行到一半，还没法提交，预计完成还需1天时间。但是，必须在两个小时内修复该bug，怎么办？幸好，Git还提供了一个stash功能，可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作<br>
> $git stash  查看工作区<br>
> 创建分支修改bug，首先确定要在哪个分支上修复bug，假定需要在master分支上修复，就从master创建临时分支<br>
>> $ git checkout master<br>
   $ git checkout -b issue-101

> 现在修复bug，需要把“Git is free software ...”改为“Git is a free software ...”，然后提交<br>
> 修复完成后，切换到master分支，并完成合并，最后删除issue-101分支
>> $ git checkout master<br>
   $ git merge --no-ff -m "merged bug fix 101" issue-101<br>
   $ git branch -d issue-101

> 回到dev分支<br>
>> $ git checkout dev<br>
   $ git status

> 工作区是干净的，刚才的工作现场存到哪去了？用git stash list命令查看。Git把stash内容存在某个地方了，但是需要恢复一下。<br>
>> 一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除<br>
   另一种方式是用git stash pop，恢复的同时把stash内容也删了

>再用git stash list查看，就看不到任何stash内容了
- feature分支
> 添加一个新功能最好新建一个Feature分支，完成后合并然后再删除feature分支
> 1、新建一个分支
>> $ git checkout -b feature-new

> 2、切回原来的dev分支
>> $ git checkout dev

> 3、突然发现这个新功能不用了，销毁新建的分支
>> $ git branch -d feature-new <br>
>> 因为新分支还没有合并，所以销毁失败<br>
>> 强行删除 $ git branch -D feature-new

- 多人协作
> 从远程仓库克隆时，就是git把本地的master分支和远程的master分支对应起来，远程仓库的默认名是origin.
> 1、查看远程仓库信息
>> $ git remote <br>
>> $ git remote -v

> 2、推送分支-将本地分支推送到远程库
>> $ git push origin master <br>
>> $ git push origin dev

> 3、抓取分支
>> 甲同学要在dev分支上开发，创建远程origin的dev分支到本地 <br>
>> $ git checkout -b dev origin/dev  <br>
>> 开发代码，将本地dev分支push到远程库，此时乙同学也对这个文件进行了修改，并试图推送 <br>
>> 推送失败，因为甲乙两人的提交的代码冲突，可以先将远程库中最新的提交抓下来，然后在本地手动合并，再推送。<br>
>> $ git pull <br>
>> 推送失败，因为乙没有指定本地dev分支与远程origin/dev分支的链接。<br>
>> $ git branch --set-upstream dev origin/dev <br>
>> $ git pull <br>
>> pull成功，但是合并有冲突，可以手动解决冲突，再push上去。<br>

> 总结：首先，可以试图用git push origin branch-name推送自己的修改；<br>
> 如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；<br>
> 如果合并有冲突，则解决冲突，并在本地提交；<br>
> 没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功；<br>
> 如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令 <br>
> git branch --set-upstream branch-name origin/branch-name。






