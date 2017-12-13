#### 问题：
部署过程出现卡死 or `SSH ERROR: Write failed: Broken Pipe`字样

#### 表象：
![](/assets/Broken_pipe.png)

#### 原因：

脚本包含重启动作
* 对端节点重启
* 对端节点网卡重启

#### 解决：

在节点重启/网卡重启 task之后，用下面task保活ssh连接
```
- name: Wait for node/NET restart
  local_action:
    module: wait_for
      host=192.168.50.4
      port=22
      delay=1
      timeout=300
```

[详见wait_for使用](http://docs.ansible.com/ansible/wait_for_module.html)