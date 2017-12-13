##通过克隆原DMK虚拟机快速生成一对新的DMK主备节点

###准备工作

    两台机器的IP和浮动IP均已经规划好。

###操作步骤

      注：在2台机器上分别执行以下操作：

####1. 在FC界面，克隆虚拟机

####2. 克隆完毕，使用VNC登陆

####3. yast进行网络配置

####4. 主备HA分别配置

#####① 根据网络信息修改配置文件

```
# vi $HA_DIR/conf/noneAllInOne/gmninit.cfg, 默认（$HA_DIR 为 /opt/ha）
deployMode=1     
haMode=2        
nodeName=APICOMDB-01   
localIP=192.144.145.161            本机IP (ifconfig查看)
localMask=255.255.255.0            子网掩码(ifconfig查看)
localGateWay=192.144.145.254        网关(route查看)
floatIP=192.144.145.163             浮动IP
remoteNodeName=APICOMDB-02
remoteIp=192.144.145.162           对端IP
haArbitrationIP=192.144.145.254    仲裁IP，和网关设置为一样的
itfName=eth0                       本机网卡(ifconfig查看)

```

#####② 配置HA

执行前先查看是否有/opt/ha/module/harm/plugin/conf.base目录

如果有,执行以下命令：

```
cp -aR /opt/ha/module/harm/plugin/conf  /opt/ha/module/harm/plugin/conf.base

然后执行：

sh $HA_DIR/tools/configHA4CI.sh

```

如果没有，执行以下命令：

```
sh $HA_DIR/tools/configHA4CI.sh

```

#####③ 查看ha状态


在dmk用户下执行：haStatus      #主节点状态都为normal时为正常

![](/assets/haStatus.png)






    
