### SSH基本知识

#### SSH加密登录和交互

![](/assets/SSH_Login_Trans.png)

#### 常用的SSH操作

##### 公钥登录

使用密码登录，每次都必须输入密码，非常麻烦。好在SSH还提供了公钥登录，可以省去输入密码的步骤。

所谓"公钥登录"，原理很简单，就是用户将自己的公钥储存在远程主机上。

**登录的时候，远程主机会向用户发送一段随机字符串，用户用自己的私钥加密后，再发回来。**

**远程主机用事先储存的公钥进行解密，如果成功，就证明用户是可信的，直接允许登录shell，不再要求密码。**

这种方法要求用户必须提供自己的公钥。如果没有现成的，可以直接用`ssh-keygen`生成一个：

```shell
ssh-keygen
```

运行上面的命令以后，系统会出现一系列提示，可以`一路回车`。  
其中有一个问题是，要不要对私钥设置口令（passphrase），如果担心私钥的安全，这里可以设置一个。

运行结束以后，在$HOME/.ssh/目录下，会新生成两个文件：id\_rsa.pub和id\_rsa。前者是你的公钥，后者是你的私钥。

这时再输入下面的命令，将公钥传送到远程主机host上面：

```shell
ssh-copy-id user@host
```

如果还是不行，就打开远程主机的`/etc/ssh/sshd_config`这个文件，检查下面几行前面"\#"注释是否取掉。

```shell
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
```

然后，重启远程主机的ssh服务。

```shell
// ubuntu系统
service ssh restart
// debian系统
/etc/init.d/ssh restart
```

远程主机将用户的公钥，保存在登录后的用户主目录的`$HOME/.ssh/authorized_keys`文件中。

> 公钥就是一段字符串，只要把它追加在authorized\_keys文件的末尾就行了。

##### SSH使用技巧一则：使用config文件创建别名

```shell
dmk@DMK01:~/.ssh> cat ~/.ssh/config 
Host ol
    HostName 172.30.16.180
    User dmk
```

```shell
dmk@DMK01:~/.ssh> ssh ol

Authorized users only. All activities may be monitored and reported.
Last login: Wed May 17 01:18:55 2017

[dmk@DMK-Euler-01 ~]$
```

> ~/.ssh/config 文件最先被载入，然后是 /etc/ssh\_config 文件

[参考](http://yysfire.github.io/linux/create-ssh-alias.html)

##### ssh-agent 和 ssh-add

其实ssh-agent就是一个密钥管理器，运行ssh-agent以后，使用ssh-add将私钥交给ssh-agent保管，其他程序需要身份验证的时候可以将验证申请交给ssh-agent来完成整个认证过程。

没有passphrase的key每次连接直接就连过去了。但是有passphrase的连接，每次都需要输入，很麻烦。

```shell
eval `ssh-agent` 或 ssh-agent bash
echo "$SSH_AGENT_PID"
echo "$SSH_AUTH_SOCK"
ssh-add
```

再登录就不是每次都需要了。

> 重新生成公私钥对，需要kill掉`ssh-agent进程`，再重新`ssh-copy-id`



