###解锁、修改sysadmin密码（非管理员请慎用）

####1. 解锁sysadmin账号

```
1. 登录到DMK主节点后台，进入目录： /pkg_repo/data/appdb

2. 执行：sqlite3 dmk_production.sqlite3       #进入数据库

3. 在数据库中依次执行以下命令：

   update users set isLock='false' where user_name='sysadmin'; 
   
   select id from users where user_name='sysadmin';        #查询sysadmin的user_id
   
   delete from lock_records where user_id='user_id';       #user_id取自上一步的结果

4. 解锁成功。

```

####2. 可以通过以下步骤在后台修改sysadmin密码

```

1. 登录到DMK主节点，进入目录：cd /opt/autodeployment/script

2. 在dmk用户下执行：ruby change_sysadmin_pass.rb

3. 依次输入：production、新密码、确认密码

4. 修改成功。

```