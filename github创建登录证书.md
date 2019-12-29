##登录证书
```
添加证书之前，还要做这么一步：
Git服务器打开RSA认证 。在Git服务器上首先需要将/etc/ssh/sshd_config中的RSA认证打开，即将sshd_config文件中下面几个的注释解开：

1.RSAAuthentication yes

2.PubkeyAuthentication yes

3.AuthorizedKeysFile .ssh/authorized_keys

这里我们可以看到公钥存放在.ssh/authorized_keys文件中。

//所以我们在/home/git下创建.ssh目录，然后创建authorized_keys文件，
# cd /home/git/
# mkdir .ssh #新建文件夹
# chmod 700 .ssh
# touch .ssh/authorized_keys  #新建文件
# chmod 600 .ssh/authorized_keys

//生成密钥
（1）、设置用户名和邮箱
        git config --global user.name '用户名'
        git config --global user.email '邮箱地址'
（2）、查看是否存在ssh keys
        cd ~/.ssh
若出现“No such file or directory”,则表示需要创建一个ssh keys。
（3）、 创建新的ssh keys
        ssh-keygen -t rsa -C "邮箱"
输入：创建的秘钥文件夹名字
        authorized_keys.  #私钥文件
        authorized_keys.pub #公钥文件
（4）、测试一下连接
        ssh -T -v git@github.com
        报错：Permission denied(publickey)
        以上信息显示连接github失败，原因是因为我们没有将新生成的密钥加到我们的gitHub里面，所以我们需要打开authorized_keys.pub文件，把里面的内容拷贝到GitHub ，打开链接 里面Setting中的ssh and GPG key中，点击new ssh key把我们公钥文件id_rsa.pub的内容粘到key中，title随意写，保存即可。

再次尝试连接：
        ssh -T git@github.com
        还是报刚才的错误，这是因为在本地计算机与 GitHub 建立连接的时候，实际上是本机计算机的 ssh-agent 与 GitHub 服务器进行通信。虽然本地计算机有了私钥，但是 ssh-agent并不知道私钥存储在哪儿。因此，要想正常使用秘钥对，需要先将私钥加入到本地计算机的ssh-agent 中（添加过程中需要输入 passphrase）

这时可以通过了:
        ssh-add ~/.ssh/authorized_keys
        如果上述命令执行后出现提示:Could not open a connection to your authentication agent.
        解决方法：eval `ssh-agent  -s`
        ssh-add ~/.ssh/authorized_keys

ssh -T git@github.com
如果出现： Hi —! You’ve successfully authenticated, but GitHub does not provide shell access. 表明git服务搭建成功！



```



##禁止Shell登录
```
编辑/etc/passwd文件
git:x:502:502::/home/git:/bin/bash  修改为：git:x:502:502::/home/git:/usr/local/git/bin/git-shell


```
