=============================================================================
安装github : apt-get install git

配置用户名和邮箱(账号的用户名和邮箱)
git config --global user.name "name"
git config --global user.email "email"
检查配置:git config --list

配置SSH密钥 (不配置密钥不可以通过URL获取 大文件通过ssh传输稳定)
ssh-keygen -t rsa -C "email"

进入github主页 在设置中添加SSH密钥 将~/.ssh/id_rsa.pub中的内容拷贝即可

=============================================================================
git本地仓库

仓库 - repository也叫版本库
可以看做一个目录,这个目录里的所有文件都由Git进行管理
每个文件的修改、删除,Git都可以进行跟踪

创建一个目录作为仓库 然后使用指令git init 目录进行初始化
该目录下创建出的新.git目录用来跟踪管理版本库

创建README.txt文件 描述仓库
执行指令 git add README.txt 将文件添加至仓库

执行指令 git commit 将仓库内容更新 可以使用参数选项-m直接编写注释

使用指令 git status 查看仓库状态
此时无内容更新

修改README.txt
再次查看仓库状态
(use "git add <file>..." to update what will be committed)
(use "git checkout -- <file>..." to discard changes in working directory)
可以观察到修改后的文件需要使用git add标记 然后get commit才会将其进行更新

========================================================================
版本回退

使用指令 git log 查看仓库修改日志
使用指令 git log --pretty=oneline 将日志信息简化为单行输出

使用git reset --hard HEAD^ 进行版本回退 //HEAD表示当前版本 HEAD^表示上个版本 多个^以此类推

========================================================================
git的版本管理流程
工作区（Working Directory）创建的目录就是一个工作区。
版本库，仓库（Repository）工作区有个隐藏目录 .git这个不算工作区，而是 Git 的版本库。
版本库里面的 index(stage) 文件叫暂存区，还有Git为我们自动创建的第一个分支 master ，以及指向 master 的一个指针叫做 HEAD

如果我们想把文件添加到Git里面时，需要分两步：
第一步是用 git add 把文件添加进去，实际上就是把文件修改添加到暂存区
第二步是用 git commit 提交更改，实际上就是把暂存区的所有内容提交到当前分支

如果要将修改但没有添加到暂存区的文件撤销回工作区状态 使用git checkout -- 文件名即可
将暂存区的文件撤销回工作区状态 使用 git reset HEAD 文件名即可
已经提交至仓库的文件只能进行版本回退

============================================================================
git远程操作

新建远程仓库并关联本地仓库
在github中创建仓库
创建完后在本地使用指令添加远程仓库
git remote add origin <email>:username/repositoryname.git
随后可以使用git push命令将本地仓库推送至远程仓库






========================================
Ubuntu 加速连接github

nslookup github.global.ssl.fastly.net 获取github.global.ssl.fastly.net地址
写入hosts文件，刷新缓存
sudo vim /etc/hosts

#github
74.86.12.173 http://github.global.ssl.fastly.net
74.86.12.173 https://github.global.ssl.fastly.net

20.205.243.166 http://github.com
20.205.243.166 https://github.com

重启网络服务
