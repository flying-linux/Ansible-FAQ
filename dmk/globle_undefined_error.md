####问题：全局配置文件不存在

![](/assets/globle_undefined_error.png)

####表象：

部署任务时，DMK报“全局配置文件不存在，请联系DMK管理员配置全局变量”

    此问题常出现在新搭建的环境上（未做全局配置）。

####解决：

#####1. 使用sysadmin账户登录DMK

#####2. 点击 “公共配置” -> “编辑” ，将下面配置项（第90行）配置为HEC、DT、CTC、OCB或TLF中的任意一个。

```
g_current_region:
  location: 'HEC'

```
#####3. 修改完成后，点击 “保存”即可。

