### 提权方式变化为su，Ansible配置和脚本需要相应的修改


#### Ansible配置修改
##### 增加`become_method=su`
#####配置文件在DMK后台路径：
/pkg_repo/playbook_sync_store/playbook/`{service_name}`/`{service_version}`/ansible.cfg
#####若服务没有自定义ansible.cfg文件，按照上述路径添加一个即可，内容如下：
```
[defaults]
forks = 20

# smart - gather by default, but don't regather if already gathered
# implicit - gather by default, turn off with gather_facts: False
# explicit - do not gather by default, must say gather_facts: True
gathering = smart

host_key_checking = False
timeout = 60
display_skipped_hosts = False

[ssh_connection]
ssh_args = -o ControlMaster=auto -o ControlPersist=120s
pipelining = True
scp_if_ssh = True

[privilege_escalation]
become_method=su
```

[ansible.cfg](http://code.huawei.com/OWL/AutoDeployment/blob/master/deploy/ansible.cfg)

#### 部署脚本修改
##### `sudo`改为`become`
```
- name: whether su is available
  shell: iptables -L
  register: iptables_info
  become: yes
```
[DMKTest](http://code.huawei.com/OWL/AutoDeployment/blob/master/FuncTest/deploy/roles/test_su/tasks/main.yml)