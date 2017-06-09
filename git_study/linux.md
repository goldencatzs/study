###ubuntu vim 方向键变成ABCD
卸载vim-tiny
>sudo apt-get remove vim-common

安装vim full
>sudo apt-get update
sudo apt-get install vim


###ubuntu apt-get设置代理

一个是“/etc/environment”，这个是系统的环境变量，里面定义了“http_proxy”等代理环境变量。另一个是“/etc/apt/apt.conf”，这个就是apt的配置，内容如下
>Acquire::http::proxy "http://172.16.0.14:3128/";
Acquire::ftp::proxy "ftp://172.16.0.14:3128/";
Acquire::https::proxy "https://172.16.0.14:3128/";

可以用“-c”选项来指定使用配置文件，也就是复制一份为“~/apt_proxy.conf”
>sudo apt-get -c ~/apt_proxy.conf update
就可以使用代理了，apt-get也有一个“-o”选项，直接跟apt-get的设置变量，就不用指定配置文件了，比如
>sudo apt-get -o Acquire::http::proxy="http://127.0.0.1:8000/" update

### ubuntu ssh
更新源列表
>sudo apt-get update

安装ssh
>sudo apt-get install openssh-server

查看ssh服务是否启动
>sudo ps -e | grep ssh

启动ssh服务
>sudo service ssh start

修改配置文件"/etc/ssh/sshd_config", 改为PermitRootLogin yes


###windows 取消禁ping
Windows防火墙->高级设置->入站规则->文件和打印机共享（回显请求-ICMPv4-In）->两个规则都启用