##DMK对接Repoman及常见问题排查方法

###一、 DMK对接Repoman

####使用sysadmin账号登录DMK，配置Repoman信息（前提是已经获得Repoman节点的认证信息），如下图：

![](/assets/dmk_repoman_setting.png)

####使用team账号登录DMK，点击：包仓库->导入，即可看到repoman包仓库的包列表，表示对接Repoman成功，如下图：

![](/assets/dmk_repoman_content.png)

####对接Repoman到此结束。


###二、 定位分析方法

####1. 提示“Repoman Server Unreachable”

    此问题通常是DMK与Repomanserver网络不通引起的
    
#####在DMK后台执行以下命令，如可以正常获取token，则表明网络OK

```
dmk@DMK01:~> curl -l -H "Content-type: application/json" -X POST -d '{"name":"VMPApiCaller","password":"VMPApiCaller12#$"}' "https://10.93.174.35:443/repoman/api/auth/user/logon/" --insecure
{
  "token": "FoEerxSObL"
}
#注意：上述命令中的ip和端口信息应用当前环境保持一致

```

#####2. 从Repoman下载包失败，可从以下两方面定位问题

```

下载包log路径：/var/log/autodeployment/delayed_job.log

失败包存放路径：/pkg_repo/data/codeBase

```





