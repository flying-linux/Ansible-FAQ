#### DMK Portal验证码刷不出来

##### 原因：

1. JAVA未正确安装

2. 虚拟机不符合规格：DMK虚拟机必须采用4u8g规格；

3. 查看后台日志：SQLite3::ReadOnlyException: attempt to write a readonly database。

##### 解决：重启DMK
`sh /opt/autodeployment/bin/dmk_monitor.sh restart`


