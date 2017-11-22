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


