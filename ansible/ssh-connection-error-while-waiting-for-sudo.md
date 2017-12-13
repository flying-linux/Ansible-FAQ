#### 问题：
ssh connection error while waiting for sudo password prompt

#### 表象：
```
TASK: [console_install | config nodejs] ***************************************
fatal: [192.144.42.249] => ssh connection error while waiting for sudo password prompt
```

#### 原因：
**第1种：**[ssh配置启用了UseDNS](/ansible/playbook task consume long time.md)

##### 第2种：[ssh timeout（UDS-LVS属于该问题）]

##### 第3种：[启用了pipelining，必须`disable 'requiretty' in /etc/sudoers](/ansible/waiting-for-a-privilege-escalation-password-prompt.md)`

##### 第4种：非英文的执行环境会导致ansible无法辨识"Password"的字样(比如中文locale环境执行ansible命令, 无法识别"密码"字样)

#### 解决：

**第1种：**

* 登录故障的目标节点
* vim /etc/ssh/sshd_config
* 显式关闭UseDNS: UseDNS no
* 重启sshd服务: service sshd restart

**第2种：**

* 增加timoeout时间，export ANSIBLE_TIMEOUT=30

* 或在ansible.cfg文件增加：
  ```
  [defaults]
  timeout = 30
  ```
  
**第3种：**

* [启用了pipelining，必须`disable 'requiretty' in /etc/sudoers](/ansible/waiting-for-a-privilege-escalation-password-prompt.md)`
  
**第4种：**

* 该场景仅针对个人安装的ansible服务器; 采用标准Euler/Suse模板安装的DMK无此问题.
* 请将ansbile执行环境的locale改成en_US.UTF-8; 
* 或者ansible-playbook命令执行前增加ANSIBLE_MODULE_LANG=en_US.UTF-8变量

---

#### [账号验证](/dmk/validate_user_guide.md)成功了吗？


