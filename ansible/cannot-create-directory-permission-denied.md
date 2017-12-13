#### 问题：
cannot create directory `/home/$user': Permission denied

#### 表象：
![](/assets/creat_dir_permission_denied.png)

#### 原因：
节点用户家目录无+x权限

#### 解决：
给目标节点家目录增加+x权限，并将当前用户的umak修改为027