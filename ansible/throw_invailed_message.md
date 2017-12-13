#### 表现
debug模式抛出大量执行信息，并提示大量`command not found`错误信息

#### 原因
限制了ssh用户的命令权限

![](/assets/ssh_user_forbid.png)

#### 解决
ForceCommnd注释起来

**重启sshd:**
`service sshd reload`