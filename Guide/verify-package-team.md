###确认软件包所属组

####适配DMK的软件包共有三种类型

```
service ：服务

3rd ： 第三方组件

security ： 系统安全补丁

确认包类型可参考下图： 在本地打开已打包的zip包，找到xxxxx.json文件，json文件中"team_name"字段的值即为当前软件包所属组。

```

![](/assets/vericy_package_type.png)


###若包类型为service（服务）时，应注意以下问题：


#####使用DMK进行部署时，必须使用team账号（team账号可由sysadmin账号创建），同时team账号必须关联软件包所属的组

#####如何确认软件包属于哪个组？

    在本地打开已打包的zip包，找到xxxxx.json文件，json文件中"team_name"字段的值即为当前软件包所属组。

![](/assets/verify_package_team.png)

#####检查当前team账号所有组

![](/assets/check_account_teams.png)

#####若所需team未关联至账号，请联系环境管理员，使用sysadmin账号给账号添加对应的team组

![](/assets/edit_account_team.png)



