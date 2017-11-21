# 1、常用命令
- *显示目录文件（list）*
> $ ls
>> first_repository/README.mdm second_repository/
- *mkdir 创建新目录（make directories）*
> $ mkdir my_document
- *cd切换目录（change directory）*
> $ cd my_document
- *pwd显示当前目录(print working directory)*
> $ pwd
>> /d/git_test/my_document
- *cp赋值文件或目录（copy）*
> $ cp /tmp/test.gz  /home/test  ##复制文件不用加选项
> $ cp -r /tmp/China /home/test  ##复制目录要加-r选项
- *mv 剪切文件、重命名（move）*
> $ mv /tmp/Beijing /tmp/Capital ##将beijing改为Capital
> $ mv /tmp/shanghai /tmp/test   ##将shanghai剪切到test目录下
- *rm删除文件或目录(remove)*
> $ rm -rf /tmp/test
- *touch创建空文件*
> $ touch /tmp/HTML5.html
- *cat显示文件内筒*
> $ cat /etc/services
> $cat /etc/issue
# 2、vim编辑器
- *首先进入Vim编辑页面*
> $ vim README.md
- *按a进入编辑模式，编辑完成后，按esc键进入命令模式么然后再按:wq，然后回车，退出保存*
