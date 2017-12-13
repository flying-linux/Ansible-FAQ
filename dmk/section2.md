#### 问题：anible软件包同步失败
提示：rsync: failed to connect to 192.144.145.46

##### 表象：

```
E:\Jenkins\workspace\rsync_DMK_ansible>echo y   | "C:\Program Files\cwRsync\bin\plink" -pw Huawei12#$ root@10.175.38.58 "rsync -auvrz --progress /pkg_repo/ci/service/DMK/2016-07-29_16-32-20 dmk@192.144.145.46::service/DMK  --password-file=/opt/passwd.txt" 
rsync: failed to connect to 192.144.145.46: Connection refused (111)
rsync error: error in socket IO (code 10) at clientserver.c(122) [sender=3.0.4]
```

##### 解决：

```
登录连接失败的节点(failed to connect to *192.144.145.46*)，切换到root，执行以下命令： 
ps -ef | grep rsync 
如果rsync进程不存在，执行 /usr/bin/rsync --daemon --config=/etc/rsyncd.conf
```

```
在定时任务中增加：
1 * * * * root /usr/bin/rsync --daemon --config=/etc/rsyncd.conf >/dev/null 2>&1

重启定时任务服务：
rccron restart
```

