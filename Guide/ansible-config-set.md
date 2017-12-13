根据DMK的使用场景和用户，DMK 2.1.2版本，对ansible配置的进行了如下修改，优化和加快部署过程。

![](/assets/ansible_config_optimization.png)

#### /etc/ansible/ansible.cfg修改内容包含`defaults`和`ssh_connection`相关项，如下：
```
[defaults]
forks = 20

# implicit - gather by default, turn off with gather_facts: False
# explicit - do not gather by default, must say gather_facts: True
gathering = explicit

host_key_checking = False
timeout = 60

[ssh_connection]
ssh_args = -o ControlMaster=auto -o ControlPersist=120s
pipelining = True
scp_if_ssh = True
```

---

#### 服务组有需求，而存在不同于上述配置的情况。
>主要是gathering，是否收集主机节点facts

#### 目的：如何让`DMK所做的优化生效`，并且让`服务组的需求也生效`？
#### 先了解下，ansible配置文件使用优先级：
```
ANSIBLE_CONFIG (环境变量)
ansible.cfg (当前目录)
~/ansible.cfg (home目录)
/etc/ansible/ansible.cfg (DMK优化的配置文件)
```

#### 根据实际情况，分为了下面2个常见场景：
##### 1、服务组需要收集使用主机的facts，比如：hostvars。

DMK优化配置后，默认关闭收集host节点“Facts”，也就是不运行`setup`模块。

**为了使这一项（gather_facts）生效，有2种办法：**

* A. 在执行的shell脚本里导入环境变量，`export ANSIBLE_GATHERING=implicit`

```
dmk@I-DMK02-98:/pkg_repo/playbook/DMKTest/1.0.3> cat test_sudo.sh 
#!/bin/bash
export ANSIBLE_GATHERING=implicit
ansible-playbook -i hosts test_sudo.yml -k -K
```

![](/assets/export_ansible_gathering_implicit.png)


* B. 在需要使用的yml脚本里设置`gather_facts: yes`

```
dmk@I-DMK02-98:/pkg_repo/playbook/DMKTest/1.0.4> cat test_sudo.yml 
---
- hosts: test_sudo
  remote_user: "{{ssh_user_by_sudo}}"
  gather_facts: yes
  roles:
   - test_sudo

- hosts: test_su
  remote_user: "{{ssh_user_by_su}}"
  roles:
   - test_su
```



##### 2、如果服务组部署脚本中已经有ansible.cfg配置文件，以CloudEye为例：
![](/assets/CES_Ansilbe_config.png)

经过测试发现，ansible使用当前目录下的配置文件，`不会加载/etc/ansible/ansible.cfg`(DMK优化的配置文件)。

##### 解决：如何既能使用DMK优化的配置文件，还能让`差异项`生效。
* 找出不同的配置项，比如：timeout想设置为20；
* 通过导入ANSIBLE_CONFIG(环境变量)使某项生效。
  - 在部署目录的x.sh脚本中增加`export ANSIBLE_TIMEOUT=20`即可。

其实，看下上面的配置文件，其实可以评估下是否真的需要，是否可用直接删掉。

DMK根据自身机器性能，进行测试优化，得到ansible配置。

大家更关注的还是第一条，需要**获取节点信息的gather如何开启收集**。