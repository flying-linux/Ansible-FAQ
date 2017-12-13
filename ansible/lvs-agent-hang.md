 ### 通过对LVS安装过程进行分段验证SSH卡死问题
 
 #### 测试结果如下：
 1. 重新安装Euler2.1，测试SSH连接，无挂死现象。
 2. 在Euler2.1系统上安装LVS所需模块，测试SSH连接，无挂死现象。
 3. 安装LVS模块后，对LVS进行配置，修改keepalived.conf文件，测试SSH连接，无挂死现象。
 4. 对操作系统内核进行配置，修改/etc/sysctl.conf文件，测试SSH连接，出现SSH挂死现象。
 5. 回退/etc/sysctl.conf文件为默认配置，测试SSH连接，无挂死现象。
 6. 经过定位，发现net.ipv4.tcp_tw_reuse开关打开了，而net.ipv4.tcp_timestamps为关闭状态，再次使用LVS安装的/etc/sysctl.conf文件配置，并 打开配置中的时间戳项（net.ipv4.tcp_timestamps = 1），测试SSH连接，已测试一个小时无挂死现象。
 7. 修改/etc/sysctl.conf文件中net.ipv4.tcp_timestamps = 0，测试SSH连接，出现SSH挂死现象（多次重试1~2分钟内必现）。
 
 #### 定位结论：
 通过测试结果可以确认：net.ipv4.tcp_tw_reuse开关打开了，而net.ipv4.tcp_timestamps未打开造成了SSH挂死现象。
 
 `net.ipv4.tcp_tw_reuse`与`net.ipv4.tcp_timestamps`需要配套使用，tcp重用开关打开后，必须打开tcp时间戳开关，否则重用时会造成挂死现象。
 
 
 #### 参数解释：
 * net.ipv4.tcp_tw_reuse =1 允许将TIME-WAIT sockets重新用于新的TCP连接，默认为0，表示关闭
 * net.ipv4.tcp_timestamps=1，时间戳，启用后在TCP的包头增加12个字节。
 
 #### 修改生效方法：
 1. 修改双方节点的net.ipv4.tcp_timestamps配置项值为1，原始配置值为0。
 2. 执行命令，生效配置：sysctl -p