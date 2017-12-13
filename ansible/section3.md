#### 问题

SSH Error: Permission denied (public key, password)

#### 原因：

* known_hosts里的fingerprint产生了变化
* 确保连接的用户ssh user为当前服务的用户
* authorized_keys权限不对（-rw-------），或者没有此文件（未分发公钥）

* 未建立互信，即分发（Distribute）公钥

#### 解决

```
echo '' > ~/.ssh/known_hosts
```

* 在账号仓库验证用户的连通性

* 在DMK server上使用debug模式（-vvvv）执行ansible-playbook命令



