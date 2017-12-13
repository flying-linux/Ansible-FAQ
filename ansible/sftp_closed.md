#### 问题：
Couldn't read packet: Connection reset by peer

#### 表象：
failed to transfer file to /home/user/.ansible/tmp/ansible-tmp-xxxx; 

Couldn't read packet: Connection reset by peer

![](/assets/reset_by_peer.png)

#### 原因：
目标节点的/etc/sshd/sshd_config没有enable sftp subsystem, 或其他手段禁用了sftp

#### 解决：

* (推荐) 方法1：在ansible-playbook命令前增加ANSIBLE_SCP_IF_SSH=True 强制使用SCP进行文件传输

* 方法2：在ansible-playbook命令执行的文件夹下为ansible.cfg增加scp_if_ssh=True的配置项
```
scp_if_ssh = True
```

* 方法3：打开目标节点的sftp

