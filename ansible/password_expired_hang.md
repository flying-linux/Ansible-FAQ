#### 问题：

DMK下发任务后，如果节点密码过期，DMK升级就卡住，持续了近1个小时，最终只能手动终止任务。


#### 表象：
![](/assets/password_expired_hang.png)


#### 原因：
远端节点虚拟机密码过期


#### 解决：
1. 部署前，希望先进行`账号验证`，保证账号可用。

    [账号验证](/dmk/validate_user_guide.md)

2. 若ansible.cfg配置开启`pipelining`的话，**任务不会卡主**，而是会提示失败信息。 

    [启用pipelining](/Guide/serviceansibleconfigset.md)
    
    ![](/assets/password_expired_pipelining_true.png)

#### 建议：
真心希望，若无必要，在playbook下不要存在ansible.cfg，默认会使用/etc/ansible/ansible.cfg配置。