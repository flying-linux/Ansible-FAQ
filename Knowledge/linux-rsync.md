#### rsync代替cp?
![](/assets/cp_rsync.png)


##### 使用rsync命令排除一个目录不被复制
备份autodeployment代码目录排除tmp目录的命令：


```
cd /opt && rsync -av --exclude autodeployment/tmp /opt/autodeployment /pkg_repo/tmp/
```

>注意：--exclude后面的路径不能为绝对路径，必须为相对路径才可以，否则出错。

#### rsync代替rm
```
mkdir -p /tmp/blank/ && rsync --delete-before -d /tmp/blank/ ${delete_path}/
```