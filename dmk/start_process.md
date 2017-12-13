###虚拟机重启后，单节点DMK进程无法自动拉起

####表象：

安装的单节点DMK，虚拟机重启后，DMK portal无法访问；

在DMK的后台查不到unicorn和ngin进程

```
ps -ef | grep unicorn

ps -ef | grep nginx

```

####原因：

DMK服务进程是由Ha自动拉起的，单节点DMK没有安装Ha，因此虚拟机重启后，单节点DMK服务无法自动拉起；


####解决：

在DMK后台执行以下命令，手动拉起进程：

```
sh /opt/autodeployment/bin/dmk_monitor.sh start

sh /opt/onframework/nginx/bin/start_nginx.sh

```

