
###ubuntu apt-get设置代理

一个是“/etc/environment”，这个是系统的环境变量，里面定义了“http_proxy”等代理环境变量。另一个是“/etc/apt/apt.conf”，这个就是apt的配置，内容如下
>Acquire::http::proxy "http://127.0.0.1:8000/";
Acquire::ftp::proxy "ftp://127.0.0.1:8000/";
Acquire::https::proxy "https://127.0.0.1:8000/";

可以用“-c”选项来指定使用配置文件，也就是复制一份为“~/apt_proxy.conf”
>sudo apt-get -c ~/apt_proxy.conf update
就可以使用代理了，apt-get也有一个“-o”选项，直接跟apt-get的设置变量，就不用指定配置文件了，比如
>sudo apt-get -o Acquire::http::proxy="http://127.0.0.1:8000/" update