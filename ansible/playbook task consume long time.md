#### 问题:

框架ConsoleFramework部署出现耗时3个小时，耗时巨大

#### 原因:
* 一般SSH`依次进行`的认证方法的是publickey, gssapi-keyex, gssapi-with-mic, password，可以ssh -v开启debug模式在连接日志看到。   

    一般用户只使用 password 认证方式，但前面3个认证过程系统还是会尝试，这就浪费时间了，也就造成SSH登录慢。

* ssh连接目标主机时会进行DNS解析， 如果本地hosts文件中解析不到ip和主机名映射就会在整个网络区搜索，关闭此功能提高连接 OpenSSH 服务器的速度。

#### 解决办法：
##### 1. 目标节点/etc/ssh/sshd_config配置，关闭GSSAPIAuth、useDNS
![](/assets/useDNS.png)

##### 重启sshd服务
`service sshd reload`

##### 2. 目标节点/etc/hosts
加入`::1`，避免ansible反复去DNS查询ip/hostname




