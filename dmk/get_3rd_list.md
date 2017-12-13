#### 1. 以普通用户（admin角色）登录DMK

#### 2. 根据版本关键字`Latest_3rdList`搜索，查看详情

![](/assets/get 3rd list.png)

#### 3. 得到dmk上的三方包列表

![](/assets/3rd_list.png)

#### 4. 若找不到所需的包，需要上传第三方包
* 获取最新的Install3rd.zip包
* 查看DMK的版本，若大于2.1.1，则支持直接通过DMK Portal上传
* 若小于2.1.1版本，则需要先上传到DMK服务器(主节点)后台的/pkg_repo目录，在解压到3rd目录
```
unzip -o /pkg_repo/Install3rd.zip -d /pkg_repo/3rd
```
