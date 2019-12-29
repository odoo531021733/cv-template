##github安装
```
//依赖库安装
2. # yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel
3. # yum install gcc perl-ExtUtils-MakeMaker

//卸载低版本的 Git
4. # yum remove git

//下载新版的 Git 源码包（我放的了  /usr/local/git 的目录下了，git是我自己mkdir的目录）
5. # cd git
6. # wget https://github.com/git/git/archive/v2.9.2.tar.gz
7. # tar -xzvf v2.9.2.tar.gz

//编译安装
8.  # cd git-2.9.2
9.  # make prefix=/usr/local/git all
10. # make prefix=/usr/local/git install

//添加环境变量
vim /etc/profile  

source /etc/profile   //使配置立即生效

//将git设置为默认路径，不然后面克隆时会报错
# ln -s /usr/local/git/bin/git-upload-pack /usr/bin/git-upload-pack 
# ln -s /usr/local/git/bin/git-receive-pack /usr/bin/git-receive-pack 

//创建一个git用户组和用户，用来运行git服务
# groupadd git
# useradd git -g git
# passwd git  #参数是用户名
# su - git  //切换git用户

```
