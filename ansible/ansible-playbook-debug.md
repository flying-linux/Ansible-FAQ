#### Ansible打开debug方法
* **推荐**，DMK portal上，失败任务可进行**Retry**，会提示选择v的个数，v越多，日志越详细
* 登录DMK后台：在ansible-playbook自行时命令后添加-vvvv，打开debug。

---
##### 打印出的详细日志，重点关注如下信息：
* 关注连接的**user**
* 关注连接的**ip**
* 关注**错误的命令**
* **ansible配置**

```
TASK: [initialize_task | delete oam user] ************************************* 
<172.30.52.10> ESTABLISH CONNECTION FOR USER: root
<172.30.52.10> REMOTE_MODULE command echo '' > /etc/security/opasswd && echo '' > /etc/security/op

<172.30.52.10> EXEC sshpass -d7 ssh -C -tt -v -o ServerAliveInterval=30 -o 
ControlMaster=auto -o CbkeyAuthentication=no -o User=root -o ConnectTimeout=10 172.30.52.10 
/bin/sh -c 'mkdir -p $HOME/.aOME/.ansible/tmp/ansible-tmp-1479912804.28-166512981787285'

<172.30.52.10> PUT /tmp/tmp6KSPPO TO /root/.ansible/tmp/ansible-tmp-1479912804.28-166512981787285/
<172.30.52.10> EXEC sshpass -d7 ssh -C -tt -v -o ServerAliveInterval=30 -o 
ControlMaster=auto -o CbkeyAuthentication=no -o User=root -o ConnectTimeout=10 172.30.52.10 
/bin/sh -c 'sudo -k && sudo -hclhqujmmoduihdq; LANG=en_US.UTF-8 LC_CTYPE=en_US.UTF-8 
/usr/bin/python /root/.ansible/tmp/ansible

fatal: [172.30.52.10] => ssh connection closed waiting for a privilege escalation password prompt
　　　　
FATAL: all hosts have already failed -- aborting
```
###### 若已经确认用户名和ip均没问题，错误信息依旧不明朗，只能登录DMK后台，再执行报错命令，获取更多详细信息。
##### 执行fatal行之前，EXEC之后的命令：

```
sshpass -d7 ssh -C -tt -v -o ServerAliveInterval=30 -o ControlMaster=auto -o 
CbkeyAuthentication=no -o User=root -o ConnectTimeout=10 172.30.52.10 /bin/sh -c 
'sudo -k && sudo -hclhqujmmoduihdq; LANG=en_US.UTF-8 LC_CTYPE=en_US.UTF-8 
/usr/bin/python /root/.ansible/tmp/ansible
```


#### 总结常见原因
* 清空浏览器缓存(`ctrl + F5`)，再次访问DMK？
* DMK或目标主机家目录满了？
* [账号验证](/dmk/validate_user_guide.md)都是成功吗？
* 在DMK后台能SSH到目标主机吗？能够使用`sudo su -`切换到root吗？
* 能够在{job_id}目录下，手动执行`xxx.sh`能够成功吗？屏显的报错信息又是什么？


#### 建议，Ansible配置文件
真心希望，若无必要，在playbook下不要存在ansible.cfg，默认会使用/etc/ansible/ansible.cfg配置。
