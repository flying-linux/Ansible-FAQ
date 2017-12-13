#### 问题：

checksum xxxxxxxxxxxxxxxx, failed

#### 表象：

![](/assets/checksum_failed.png)

#### 原因：
目标节点磁盘不足

#### 解决：
登录目标节点，df -Th查看，清理释放空间。