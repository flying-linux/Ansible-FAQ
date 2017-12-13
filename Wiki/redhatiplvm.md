## RedHat环境验证安装HA

### 环境准备

* FC创建2台Euler的VM
* VNC登录，绑定IP

```
[root@localhost ~]# vi /etc/sysconfig/network-scripts/ifcfg-eth0 
BOOTPROTO="static"
...
IPADDR="172.30.16.181"
NETMASK="255.255.255.0"
GATEWAY="172.30.16.1"

[root@localhost ~]# service network restart
```

* 在FC挂载500G磁盘到虚拟机
* 登录VM，挂载磁盘给DMK的数据盘/pkg\_repo

```
# 查看可用磁盘
[root@localhost ~]# fdisk -l

# 可用磁盘为/dev/xvde，挂载此磁盘
[root@localhost ~]# pvcreate /dev/xvde
  Physical volume "/dev/xvde" successfully created
[root@localhost ~]# vgcreate dmk /dev/xvde
  Volume group "dmk" successfully created
[root@localhost ~]# pvs
  PV         VG      Fmt  Attr PSize   PFree  
  /dev/xvda2 euleros lvm2 a--   39.50g      0 
  /dev/xvde  data    lvm2 a--  500.00g 500.00g

# lvcreate -l +100%FREE <volume_group> -n <logical_volume>
[root@localhost ~]# lvcreate -l +100%FREE dmk -n data
  Logical volume "data" created.
[root@localhost ~]# lvs
  LV   VG      Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  data dmk     -wi-a----- 500.00g                                                    
  root euleros -wi-ao----  39.50g

[root@localhost ~]# mkfs.ext4 /dev/mapper/dmk-data
[root@localhost ~]# groupadd dmk && useradd dmk -g dmk -m && mkdir /pkg_repo
[root@localhost ~]# chown -R dmk:dmk /pkg_repo
[root@localhost ~]# vi /etc/fstab
/dev/mapper/dmk-data /pkg_repo ext4 nodev,nosuid,noatime,nodiratime,data=writeback,errors=panic 1 2

[root@localhost ~]# mount -a
```
