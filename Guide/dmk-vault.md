#### DMK-Vault特性

##### 引入原因

由于安全限制，配置文件中不允许使出现明文密码、秘钥等敏感信息。

##### 原理：

DMK-Vault是基于ansible的Vault进行封装优化，可以像使用其他普通变量一样直接引用密码变量，明文密码的加解密由DMK完成。


##### 限制：

目前DMK仅对配置文件做了处理，该特性也仅对适用于出现在配置文件中的明文密码。


##### 使用方式：

配置文件中使用此方式：
`password: 'dmk_vault{{Huawei@123}}'`

###### 部署前：
![](/assets/vault_before_deploy.png)

###### 部署后：
![](/assets/vault_after_deploy.png)


##### 目前已经使用的服务
* ELB
* RDS
* SCC
* WorkSpace
* ...