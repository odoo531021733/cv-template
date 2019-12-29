##使用git命令把代码放到github上
```
1、把本地创建的仓库，push到github远程仓库上：
（1）、首先登陆github,创建一个名为cv-template的repositories，克隆ssh地址;
（2）、创建仓库目录：
	cd /home/git
	mkdir cv-template
	cd cv-template
	git init  //初始化git仓库
（3）、配置git仓库的用户：
	git config --global user.name "github注册的用户名"
	git config --global user.mail "github注册的邮箱"
（4）、添加远程地址：
	git remote add origin git@github.com:github注册的用户名/github创建的仓库名.git
（5）、在cv-template仓库目录下，创建文件README：
	echo "readme" > README
	git add README  //添加到git可管理文件跟踪中
（6）、提交到本地仓库：
	git commit -m 'first commit'   //first commit 只是作为描述，方便log查询，不可省略
（7）、再push到远程仓库上
	git push -u origin master   #-f是强制上传
	git push -k origin master   #是拉取

查询git提交日志：git log
查看git状态:git status

【注】如果后面又对本地仓库中添加了一些代码文件，可以通过以下命令提交：
# cd cv-template
# git add .   
add后面加了一个点，是想要提交所有文件，如果想提交指定的文件，可以写文件名
# git commit –m “NowToDo_v1.0版本信息”
# git push -u origin master


2、本地没有创建仓库，而在github上创建了一个test空仓库
（1）、将远程的空仓库克隆到本地：
	cd /home/git
	git clone git@github.com:账号名/test.git
	执行后会在当前目录生成一个github远程仓库名称的目录，再进入这个目录里面会自动创建.git目录；
（2）、配置git全局参数：
	git config --global user.name 'github注册的用户名'
	git config --global user.email 'github注册的邮箱'
	git congit --list 
（3）、添加git跟踪文件：
	在当前目录里面，写代码例如：在其目录下添加文件readme.txt
	git add readme.txt
（4）、提交到仓库管理器中
	git commit -m '提交的信息标签'
（5）、把本地仓库中的文件提交到github远程仓库中：
	git push origin master

在github上可验证文件是否存在。


```
