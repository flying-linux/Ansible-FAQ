#### 问题：

ssh connection closed waiting for a privilege escalation password prompt

#### 表象：

```
TASK: [console_install | config nodejs] ***************************************
fatal: [192.144.42.249] => ssh connection closed waiting for a privilege escalation password prompt
FATAL: all hosts have already failed -- aborting
```

#### 原因：

1. ssh到目标主机，执行sudo su - root，查看是否能够切到root用户下。

    * 如果不能就是sudoers标配置错误，导致sudo su - root无法切换至root用户。
    * 如果不能，尝试使用su - root，查看是否可用切换至root用户。

2. sudo开启需要tty终端。

#### 解决：

1. 登陆FC，使用VNC以root登陆，执行如下命令检查`/etc/sudoers`文件语法：`visudo -c`。

    若目标节点使用su切换root，则playbook中希望通过使用root执行的命令，由`sudo: yes`修改为如下：

    ```
    become: true 
    become_method: su
    ```

2. 关闭tty终端，即：注释掉 Default requiretty 一行

    ```
    visudo
    # Default requiretty
    ```

---

#### [账号验证](/dmk/validate_user_guide.md)成功了吗？



