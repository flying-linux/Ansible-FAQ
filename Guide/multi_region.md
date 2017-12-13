###多Region
####一、多region功能的介绍

   多region就是将用户操作的环境定义为主region即Local，其他环境定义为从region即添加region时里填写的名称，主region上的用户可以既在主region上建立部署时所用的账号，也可以通过主region远程建立从region上的部署所用的账号。主region的用户可以通过repoman给本地环境即Local导入安装包，也可以远程给从region的环境导入安装包，主region的用户可以给本地环境即Local实行部署，也可以远程给从region的环境实行部署。

####二、多region的添加指导
#####1. 确认本地环境与从region环境网络是否通畅，防火墙是否设置正确，保持环境的联通性
#####2.	以sysadmin的用户身份登录DMK,点击Regions-Add Region，输入Name（名称可以自定义无限制）与DMK Url（这个必须是其他DMK环境的网址，例如：https://ip:8443/,请务必确保环境是联通的），点击OK，添加成功后会显示环境联通状态。
 
 
 
####三、多region的账号仓库添加账号的指导
多region部署时可以通过以下方式给本地和远程region建立新账号。
#####1.	给本地即Local环境添加账号
  
#####2.	给其他region环境添加账号
首先，证明Beta-162region的环境下只有一个DMK组别的账号。 
其次，通过Local即主region查询到Beta-162region的环境下组别权限是DMK的账号信息。
 
最后，通过本地的环境远程在Beta-162region的环境下建立新的账号
 
下图为通过本地环境远程在Beta-162region的环境下建立新的账号成功的提示信息。
 
下图为Beta-162region的环境下已经新增账号的证明。
 
####四、多region的包仓库使用repoman下载包和本地上传包的指导
多region部署时所用到的包可以通过以下两种方式获取。

```
1.	使用repoman下载包

2.	本地上传包 

```
 
####五、多region部署指导

![](/assets/multi_region1.png)
![](/assets/multi_region2.png)


####六、多region部署的时候可能遇到的问题
部署的时候发现没有可用的账号，请参考‘多region的账号仓库添加账号的指导’。
部署的时候发现没有可用的安装包，你可以通过repoman下载的方式或者多个region分别本地上传包的方式提供安装包，实施步骤请参考‘多region的包仓库使用repoman下载包和本地上传包的指导’。
部署的时候发现没有所要选择的region选项，首先,请确认Local的Regions里是否已经添加了该region且状态是否为![](/assets/multi_region3.png)
。其次,如果已经确认Local的Regions里已经添加了该region且状态是否为![](/assets/multi_region3.png)
。那么请确认该region环境下是否有该版本的包，如果没有请使用repoman远程给该region环境下载包或者在这个region环境上上传包。

