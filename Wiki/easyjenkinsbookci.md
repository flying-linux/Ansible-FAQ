#### 安装Jenkins

##### 1. [下载Jenkins安装包和插件打包文件](http://code.huawei.com/GitlabAutoTest/jenkins_ci/blob/master/myjenkins.rar)

##### 2. 解压，把里面的jenkins.war包传到服务器

##### 3. 运行 java -jar jenkins.war

CI就建好了，通过 http://ip:8080/ 访问

>也可以自定义端口号

>java -jar jenkins.war --httpPort=9191

4. 安装插件（有依赖顺序）

![](/assets/jenkins_plugin_order.png)

---

#### 为Book工程增加Jenkins自动部署
##### 1. Jenkins服务器和CodeClub建立SSH认证

http://3ms.huawei.com/hi/blog/22388_2168171.html

[参考](http://pages.huawei.com/codeclub/guides/git_ssh_key)

##### 2. Jenkins新建job

[Git如何集成Jenkins](http://3ms.huawei.com/hi/blog/22388_2168171.html)

* 新建了2个job，一个用于集成测试，在合入前可以看到结果。
* 另外一个job是更新生产环境的代码，对外提供用，只有master分支有变化，才会触发重新部署。
* 启动jenkins
```
screen -S jenkins
java -jar /pkg_repo/jenkins/jenkins.war
ctrl a d
```

##### 3. 配置Jenkins CI
![](/assets/Jenkins_CI_Config.png)


#### 其他知识
##### Jenkins CI和webhook的区别
```
Jenkins CI只支持push events触发构建，webhook还可以支持merge request events触发构建；
但是只有Jenkins CI触发构建能返回构建状态，webhook不会返回；
Jenkins CI体现好看点。
```

##### 后台构建脚本

[记录](http://code.huawei.com/snippets/634)
