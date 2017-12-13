##DMK账号过期特性可关闭、可修改过期时间

###一、修改账户过期时间。DMK默认过期时间为90天，根据以下步骤可修改此时间。

####1. 分别在DMK主备节点修改文件 /opt/autodeployment/config/initializers/constants.rb，将USER_PWD_UPDATE_PERIOD 的值改为期望值（过期时间）;

![](/assets/USER_PWD_UPDATE_PERIOD.png)

    注意：主备节点都必须修改。
    
####2. 重启DMK进程。使用dmk用户登录至DMK主节点，执行以下命令重启DMK进程：

    sh /opt/autodeployment/bin/dmk_monitor.sh restart

####3. 修改完成，查看主备节点是否正常。


![](/assets/haStatus.png)

    主节点状态为normal时为正常

###二、 关闭账号过期特性。操作如下：

####1. 分别在DMK主备节点修改文件：/opt/autodeployment/config/environment.rb，将 USER_PWD_UPDATE_TRIGGER 的值置为false （关闭）

![](/assets/USER_PWD_UPDATE_TRIGGER.png)

####2. 执行（一）中的第2、3步





