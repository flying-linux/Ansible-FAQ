#### Account Validate使用指南
##### 使用指导：

![](/assets/account_validate.png)


##### 说明：
* 验证的目标主机，多个使用英文逗号（,）分隔
* root有2中切换方式

##### Validate策略：


* ping：检测网路/路由是否相通，检测命令就是`shell的ping`；
* ssh：检测ssh用户和密码正确性，是否可以通过ansible连接到目标主机；
* root: ssh验证OK的节点，再验证root密码是否正确，root切换方式是否正确。
    * 切换方式有2中选择：sudo和su
    * 对于ssh验证失败的节点不再进行root验证，以减少ansible连接次数，降低账号被锁概率
    
    
#### FAQ
##### Validate的验证通过，但是部署报错”Authorized failure“

**原因：**
* 部署的时候使用的用户名是自己配置的
* validate的时候，使用的ssh用户为Account的user name配置值

所以，有可能真正部署的时候使用的用户可能配置的remote_user(ssh_user)并不是Account指定的user name。
