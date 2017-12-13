#### 1. 问题描述：

欧拉自带python版本（2.7.5）高于之前suse使用的版本（2.6.9），Ansible对yml文件的解析严格了，遇到如下报yml语法的问题。

#### 2. 举例说明：

##### 2.1 Tab引起

1. MarketPlace碰到的问题**报错信息如下**：  
   ![](/assets/tab_error.png)

2. 根据报错提示，查看config_pri_sla_db.yml文件的`第一行第四列`，发现此处为tab键引起的问题，删除tab空行即可。

##### 2.2 shell模块转义引起

![](/assets/shell_sed_sysntax_error.png)

**修改解决：去掉反斜杠**

```
shell: "sed -i \'/dns_monitor.py/d\' /etc/crontab"
```

改为：

```
shell: sed -i '/dns_monitor.py/d' /etc/crontab
```

#### 3. 重要 - 单个排查方式：

大家`不用真正的在节点上跑自己的脚本`，只需要通过如下方式进行语法检查playbook下所有的**\*.yml文件**即可。

```
ansible-playbook -i hosts config_pri_sla_db.yml --syntax-check
```

删除tab前：

![](/assets/before_edit_check.png)

修改后：

![](/assets/after_edit_check.png)

#### 4. 重要 - 批量排查方式：

Beta环境已经是欧拉系统，登录后台测试，Ops可联系我获取后台节点信息。

如下命令可以快速检查playbook下的所有部署yml文件。

```
1. UI上传软件包
2. 登录DMK后台节点
3. cd /pkg_repo/playbook/{service}/{version}
4. find . -maxdepth 1 -name '*.yml' ! -name '_actions_spec.yml' | xargs ansible-playbook -i hosts --syntax-check
```
![](/assets/multi_file_check.png)

> DMK切换欧拉的软件包发布时间：6月30号。



