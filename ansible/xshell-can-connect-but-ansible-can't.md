###一、Xshell能正常连接但是通过DMK却认证失败
####问题描述：
xshell连接目标主机使用的是`tty`方式，但DMK连接目标主机使用的是`no-tty`方式，因此xshell能成功连接目标节点不表示DMK也能成功连接，具体的问题需要具体分析。
####打印错误日志：
* 方式一：DMK账号验证功能，“账号仓库”—>选择账号—>“验证”，选择正确的`Root切换`方式（与实际目标主机保持一致），若验证失败会有错误日志；

* 方式二：使用创建好的account账号直接进行部署，部署失败后在任务`详情`页面最下面，点击“重试”，选择V的个数（V越多日志越详细）；


####问题排查：
常见的错误信息如下（链接），请对号入座：

1. [Authentication Failure](/ansible/section1.md)；
   
2. [Incorrect become password](/Incorrect become password)；
   
3. [Connection reset by peer](/Connection reset by peer)；

4. [SSH Error: Permission denied(public key, password)](/SSH Error: Permission denied(public key, password))；

5. [ssh connection closed waiting for a privilege escalation password prompt](/ssh connection closed waiting for a privilege escalation password prompt)；

6. [ssh connection error while waiting for sudo password prompt](/ssh connection error while waiting for sudo password prompt)；

7. 更多。大家可以用错误关键字在本页面左上角进行搜索，会有你意想不到的惊喜。。。

###二、账号验证通过，但是部署时认证失败

####问题描述：

账号验证通过，但部署时却认证失败，此问题多数是由于服务`部署脚本`中指定的用户名与所选account账号中密码不匹配引起的。

`注：DMK部署任务时，只用到了account中的密码，用户名是在playbook脚本或配置文件中指定的。`

####如何确认部署脚本中使用的是哪个用户？

#####方法一（推荐）：使用“重试”打印出详细日志

部署失败后，点击页面最下面的“`重试`”，选择`-vvvv`。

如下例，`ESTABLISH CONNECTION FOR USER: dmk`表明使用的用户是dmk：

```
......
TASK: [ping] ****************************************************************** 
<192.144.145.49> ESTABLISH CONNECTION FOR USER: dmk
<192.144.145.49> REMOTE_MODULE ping
......

```

#####方法二：看部署脚本

目前部署脚本可在两个地方指定用户，如下：

① xxx.yml文件中，文件在DMK后台的位置：`/pkg_repo/playbook_sync_store/playbook/{service_name}/{version}`

如下例，`remote_user`指定了用户名dmk：


```
- name: rollback dmk
  hosts: dmk
  remote_user: '{{user_name}}'
  roles:
    - rollback 
```
② host配置文件,文件在DMK后台的位置：`/pkg_repo/playbook_sync_store/playbook/{service_name}/{version}`

如下例，`ansible_ssh_user`指定了用户名dmk：


```

[dmk]
primary ansible_ssh_user={{user_name}} ansible_ssh_host={{primaryIp}}
standby ansible_ssh_user={{user_name}} ansible_ssh_host={{standbyIp}}

```

请根据以上介绍的方法确认用户，切记：account账号中配置的密码必须与部署脚本指定的用户相匹配。






