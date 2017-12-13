##修改DMK的浮动IP

###若DMK的浮动ip被占用或者希望修改浮动ip，需要如下几步。

####1. 分别在DMK主备节点执行以下操作

```
   
1.  vim /opt/ha/conf/noneAllInOne/gmninit.cfg      #修改floatIP的值即可。
    
2.  sh /opt/ha/tools/configHa4CI.sh                #root下执行，使配置生效。

```
![](/assets/modify_floatip.png)

####2. 修改Nginx配置文件（主、备）

```

vi /opt/onframework/nginx/conf/nginx.conf          #将文件中的所有原浮动IP都改为新IP。

```

####3. 在主节点重启Nginx服务

```
sh /opt/onframework/nginx/bin/nginx_monitor.sh restart

```