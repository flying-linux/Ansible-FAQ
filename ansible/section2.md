### Incorrect become password

#### 表现：

```
fatal: [primary] => Incorrect become password
```

#### 可能原因如下：

1. root密码错误

2. root帐户被锁

3. 目标节点ssh用户切换到root时使用su切换，不支持sudo su，root切换方式错误

#### 第三种情况的解决办法

希望通过使用root执行的命令，由`sudo: yes`修改为如下：
```
become: true 
become_method: su
```


#### [账号验证](/dmk/validate_user_guide.md)成功了吗？



