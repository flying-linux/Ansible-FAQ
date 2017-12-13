#### 问题：
[ansible-playbook随机卡死问题汇总
](http://code.huawei.com/OWL/AutoDeployment/issues/1924)

#### 解决：

##### [1. LVS相关的卡死](/ansible/lvs-agent-hang.md)

![](http://code.huawei.com/OWL/AutoDeployment/uploads/1460fb85ed240b2a8a6a47342b7c9069/image.png)


##### 2. udslvs部署EulerOS补丁卡死
###### 遇到udslvs的类似问题, 确保自己机器传包给自己没问题(以10.34.21.129为例）。
```
如下均在udslvs节点操作即可：
1. 免密码设置: ssh-copy-id udslvs@10.34.21.129
2. 验证ssh是否会卡死: count=0 && while true; do sleep 1; ssh udslvs@10.34.21.129 "echo $count" ; count=$(($count+1)); done
3. 验证给自己scp包是否卡死: scp xxx.tar.gz udslvs@10.34.21.129:~
```

##### [3. 密码过期导致的卡死](/ansible/password_expired_hang.md)

##### 4. account未配置sudo的卡死
**解决：**部署前，可以进行[账号验证](/dmk/validate_user_guide.md)，尽可能的保证部署不是因为账号密码错误引起的。


##### 5. 服务部署任务卡死在中途，不动了。
* CES（廊坊出现一次）
* RDS（私有云出现一次）

SSH连接不稳定，突然中断，但是ControlPersist设置为1800秒（DMK目前默认ansible的配置为120秒），导致任务连接一直存在。

```
解决：
1. stop任务
2. 重新下发
```
