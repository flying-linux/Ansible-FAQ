#### 问题：
分发公钥或部署失败出现交互`add host's fingerprint`

#### 表象：
![](/assets/host_key_checking.png)

#### 原因：
未关闭ansible的主机检查

#### 解决：
修改ansible.cfg

```
# uncomment this to disable SSH key host checking
host_key_checking = False
```
