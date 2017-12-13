### DMK支持ELB使用跳板机功能

#### 1. 排查判断跳板机能不能使用？

```
ssh username@目标机器ip -p 22 -o ProxyCommand='ssh -p 22 username@跳板机ip -W %h:%p'
```

#### 2. 检查配置文件

```
Host jumper   #任意名字，随便使用
    HostName 192.168.1.1   #这个是跳板机的IP，支持域名
    Port 22      #跳板机端口
    User username_proxy       #跳板机用户
    IdentityFile ~/.ssh/id_rsa #访问跳板机的密钥

Host elb      #同样，任意名字，随便起
    HostName 192.168.1.2  #真正登陆的服务器，不支持域名必须IP地址
    Port 22   #服务器的端口
    User username   #服务器的用户
    ProxyCommand ssh username_proxy@jumper -W %h:%p
    IdentityFile ~/.ssh/jumper_id_rsa  #对应跳板机的密钥位置(需要将跳板机的密钥拷贝到这台机器上) 

Host 10.10.*.*      #可以用*通配符
    Port 22   #服务器的端口
    User username   #服务器的用户
    ProxyCommand ssh username_proxy@jumper -W %h:%p
```
