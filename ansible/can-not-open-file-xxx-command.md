#### 问题：

失败关键信息：

can't open file '/xxx/.ansible/tmp/ansible-tmp-xxx/command': [Errno 2] No such file or directory


#### 表象：
![](/assets/can_not_open_file_command.png)



#### 可能原因：

* PUT没有成功，command文件没有成功送到目标主机；
* 目标主机文件没有权限；

#### 解决：

onframework用户的家目录下.bashrc文件里面增加了这个：umask 027，把这一行去掉就OK了。

