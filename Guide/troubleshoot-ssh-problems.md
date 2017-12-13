使用ansible部署的过程中，经常出现各种由于SSH引起的问题。下面是一些排查过程和思路。

![](/assets/account_validate_failed.png)

#### 普通账号验证

使用普通业务账号连接并执行命令

```
[root@localhost DMK_Euler]# ssh -l dmk 172.30.16.181 -t 'echo $(whoami)'

dmk@172.30.16.181's password: 
dmk
Connection to 172.30.16.181 closed.
```

#### root账号验证
使用普通账号连接，`sudo + cmd`方式验证root账号

```
[root@localhost DMK_Euler]# ssh -l dmk 172.30.16.181 -t 'sudo echo $(whoami)'

dmk@172.30.16.181's password: 
[sudo] password for root: 
dmk
Connection to 172.30.16.181 closed.
```


---

##### 疑问：ansible的`become_method`有`sudo和su`，这2个有什么区别，具体该如何区分使用？

`become：yes`来激活特权提升


* su是switch user，需要切换到的用户的密码
* sudo是当前用户临时获得root权限，执行用户还是普通用户，一般不需要root密码。

  sudo 在 UNIX 和 Linux 系统上使用，用于`提供特权升级`。

  但是我们做了安全加固，修改了`sudoers`文件，取消注释`Defaults targetpw`，需要输入root密码。


查看官方文档，[Ansilbe特权提升](http://ansible-tran.readthedocs.io/en/latest/docs/become.html?highlight=become)


##### 加固后的系统不允许使用`su - root`切换到root，只能使用`sudo su -`

su 的用法：su [OPTION选项参数] [用户]
-, -l, --login 登录并改变到所转换的用户环境；
-c, --commmand=COMMAND 执行一个命令，然后退出所转换到的用户环境；

```
[dmk@localhost ~]$ su - root -c 'uptime'
Password: 
su: Permission denied

[dmk@localhost ~]$ sudo su - root -c 'uptime'
[sudo] password for root: 
 19:36:40 up  1:55,  1 user,  load average: 0.15, 0.05, 0.06
```