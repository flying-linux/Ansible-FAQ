### 登录server后台

```
# ssh root@10.154.68.45
```

### 查看后台已经启动的screen

```
# screen -ls
There are screens on:
    108007.master_gitbook    (05/11/2017 05:37:01 PM)    (Detached)
    107858.master_gitbook    (05/11/2017 05:36:13 PM)    (Detached)
    107742.jenkins    (05/11/2017 05:35:52 PM)    (Detached)
3 Sockets in /var/run/screen/S-root.
```

### 恢复，并启动

```
screen -r _pid_
```

### 启动jenkins

```
# screen -S jenkins
# java -jar /pkg_repo/jenkins/jenkins.war
# ctrl + a  d
```

### 启动master gitbook（4000）

```
# screen -S master_gitbook
# sh /pkg_repo/script/build.sh master
# ctrl + a  d
```

### 启动test gitbook（5000）

```
# screen -S test_gitbook
# sh /pkg_repo/script/build.sh
# ctrl + a  d
```



