#### 问题：
KeyError：getpwdnam(): name not found: xxx



#### 表象：
gather facts的时候出现下面问题(图1); xshell可以登录, 但输入 id或whoami 没有名字只有uid(图2)


![](http://code.huawei.com/OWL/AutoDeployment/uploads/bb57a2d7a62dd7eb3510574595f83c95/image.png)

![](http://code.huawei.com/OWL/AutoDeployment/uploads/4157b5db8ab51ca2bd6bd75ec06db56e/image.png)

#### 原因：
 
1. User 创删出过错, 损坏了系统文件
2. /etc/passwd和/etc/nsswitch.conf 权限有问题

#### 解决：
1. 可以尝试重启解决
2. 最小权限640, 属root:root
