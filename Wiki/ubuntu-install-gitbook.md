### 安装nodejs和npm
[NodeJs gpg-key](http://rnd-mirrors.huawei.com/helps/nodejsmirror)
```
root@ubuntu:/pkg_repo# vi nodejs-gpg-key
root@ubuntu:/pkg_repo# gpg_key='nodejs-gpg-key'
root@ubuntu:/pkg_repo# gpg --import ${gpg_key} && gpg --fingerprint && apt-key add ${gpg_key}

root@ubuntu:/pkg_repo# vi /etc/apt/sources.list
deb http://rnd-mirrors.huawei.com/nodejs/node_4.x trusty main
deb-src http://rnd-mirrors.huawei.com/nodejs/node_4.x trusty main

root@ubuntu:/pkg_repo# apt-get update
root@ubuntu:/pkg_repo# apt-get install nodejs

root@ubuntu:/pkg_repo# nodejs -v
v4.2.6
root@ubuntu:~# npm -v
2.14.12
```
### 安装gitbook
```
root@ubuntu:/pkg_repo# npm config rm proxy
root@ubuntu:/pkg_repo# npm config rm http-proxy
root@ubuntu:/pkg_repo# npm config rm https-proxy
root@ubuntu:/pkg_repo# npm config set no-proxy .huawei.com
root@ubuntu:/pkg_repo# npm config set registry http://rnd-mirrors.huawei.com/npm-registry/

root@ubuntu:/pkg_repo# npm install -g gitbook-cli
```

### 上传代码，启动
```
root@ubuntu:/pkg_repo/book# screen

# 安装插件
root@ubuntu:/pkg_repo/book# gitbook install

# 查看build是否通过
root@ubuntu:/pkg_repo/book# gitbook build

# 启动
root@ubuntu:/pkg_repo/book# gitbook serve
```