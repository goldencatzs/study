git常用命令
=========
由于git为分布式版本控制系统，安装完git后，需设置用户名及邮箱，这台机器上所有的git仓库都会使用这个配置，也可以对某个仓库指定不同的用户名和邮箱。

>git config --global user.name "username"
git config --global user.email "email@xxx.com"

设置代理
>git config --global http.proxy http://proxyuser:proxypwd@proxy.server.com:8080

github的SSH配置
--
1.	查看是否已经有了ssh密钥：

>cd ~./ssh

2.	生成密钥：

	>ssh-keygen -t rsa -C "email@xxx.com"

	根据提示可输入要保存密钥的地址及密码，如不需要设置，直接按回车，保存在默认路径下，没有密码。

	在提示的路径下可以找到两个文件：id_rsa和id_rsa.pub

3.	添加密钥至ssh:

	>ssh-agent -s
	>ssh-add ~/.ssh/id_rsa
		
		如果执行该命令失败，如显示：Could not open a connection to your authentication agent.可以先执行eval \`ssh-agent\`再执行下述命令即可

4.	添加ssh key至账户：

	>clip < ~/.ssh/id_rsa.pub

	拷贝id_rsa.pub中的内容至剪贴板

5.	拷贝key至github:

	settings->SSH keys->Add SSH key->填写title和key->Add key

6.	测试连接：

	>ssh -T git@github.com

附：[github官方说明](https://help.github.com/articles/generating-ssh-keys/)链接

>注：如果默认ssh-key的路径中有中文字符，会导致保存失败的情况，此时可以通过设置HOME环境变量来修改git默认查找ssh-key的路径：

>编辑git安装目录下的etc/profile文件，如：C:\Program Files\Git\etc\profile
>HOMEPATH="\c\directory\"
>
>可能没有权限保存profile文件，只需另存为，然后将文件拷贝到该路径下即可，重启git bash运行env命令，即可看到home环境变量已修改

git基本操作
---
查看帮助

>git --help 会列出git常用命令及其解释，对于具体命令的查看类似，如：git log --help

获取源码：

>git clone 仓库ssh路径git@github.com:xxx/xxx.git

仓库初始化：

>git init

关联本地仓库与远程仓库

>git remote add origin git@github.com:用户名/仓库名.git


将服务器项目与本地项目合并

>git pull

提交代码至远程

>git pull --rebase #确保当前本地的代码为最新，避免冲突
git push origin xxx

向git库添加文件

>git add xxx       #添加单个文件
git add .	       #添加所有文件，添加至stage状态
git add [path]     #把对应目录或文件添加至stage状态

从git库删除文件

>git rm xx
>git rm -r xx/

撤消修改

>git checkout -- filename 撤消对某文件的修改

恢复至某版本

>git reset --hard 哈希值 回到指定版本
git reset 将所有stage文件的状态改为非stage

向版本库提交变化

>git status 查看代码库状态
>git commit -m "xxx" 添加简单提交信息，引号内为注释
>git log 查看版本信息，可选用参数git 
>git log --pretty=oneline 将commit信息简单显示为一行
>git show 1da4251a26b1056382af96b2f8315d87d60d0ceb 

显示指定版本的修改，如果不写版本号，显示最后一次提交信息

##分支管理
创建分支

>git branch xxx

删除本地分支

>git branch -d xxx

删除远程分支

>git push origin --delete <branchname>
git push origin :<branchname>

重命名本地分支

>git branch -m branchA branchB


切换分支

>git checkout xxx

查看分支

>git branch
>git branch -a 查看所有分支，包括远程


将分支A与分支B合并

>git checkout branchA
>git merge branchB (将分支B merge至分支A)

推送本地分支

>git push origin branchA

