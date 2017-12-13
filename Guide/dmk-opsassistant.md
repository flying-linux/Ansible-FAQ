###DMK对接OpsAssistant指导书

运维助手对接DMK需要手动在DMK后台配置白名单，配置方法如下：

####1. 分别使用dmk账户登录DMK的主、备节点后台，修改件/opt/autodeployment/config/environment.rb，将运维助手的IP添加至白名单，如下图所示：

![](/assets/OpsAssistant.png)


##### 注：两个节点都要修改。

####2.	在DMK主节点执行命令：

    sh /opt/autodeployment/bin/dmk_monitor.sh restart

####3.	配置完成，使用运维助手访问DMK。

