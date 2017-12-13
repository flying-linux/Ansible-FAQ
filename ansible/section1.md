#### Authentication Failure

#### 表现：
```
fatal: [primary] => Authorized failure
```

#### 可能原因如下：

  1. ssh密码错误。请检查创建account账号时是否输入了正确的密码
  
  2. 用户名错误

  3. ssh帐户被锁

  4. ssh连接时账号错误，可通过debug查看ssh连接时具体使用的SSH账户
  ```
  ssh -vt user@host_ip
  ```

#### [账号验证](/dmk/validate_user_guide.md)成功了吗？
