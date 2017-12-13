#### 问题：
SSH ERROR: data could not be sent to the remote host. Make sure this host can be reached over ssh


#### 表象：
* 第一种情况，**开始执行**就报此错：
![](/assets/ssh_auth_failed.PNG)

* 第二种情况，**执行到某一步**报此错：
![](/assets/ssh_timeout.png)

#### 原因：

* 第一种情况原因：

  **host主机鉴权失败**

###### pipelining=True时的提示信息
```
<192.145.48.80> ESTABLISH CONNECTION FOR USER: ecm
　
fatal: [console1] => SSH Error: data could not be sent to the remote host. 
Make sure this host can be reached over ssh 
　　
PLAY RECAP ********************************************************************
    to retry, use: --limit @/pkg_repo/data/jobs/xxx/install.retry
　　
console1                   : ok=0    changed=0    unreachable=1    failed=0
　　

GATHERING FACTS ***************************************************************
<192.145.48.80> ESTABLISH CONNECTION FOR USER: ecm
```
　　
###### pipelining=False时的提示信息

```
fatal: [console1] => Authentication failure. 
TASK: [jdk | create directory used for storing package] ***********************
FATAL: no hosts matched or all hosts have already failed -- aborting
```

* 第二种情况原因：

  **任务执行时间过长**，超过SSH的ControlPersist=2分钟（DMK优化后的配置），默认1分钟
  ```
  ssh_args = -o ControlMaster=auto -o ControlPersist=120s
  ```
  
#### 解决：
* 第一种情况

  * **host主机鉴权失败**，ansible连不过去。确认部署的hosts能够通过DMK后台正常连接过去，[账号验证](/dmk/validate_user_guide.md)成功了吗？
  
  * 使用`ANSIBLE_SCP_IF_SSH=y`
  
    [参考](https://github.com/ansible/ansible/issues/13401)


* 第二种情况

  长任务，将任务异步话，并轮询

  ```
  tasks:

  - name: simulate long running op (15 sec), wait for up to 45 sec, poll every 5 sec
    command: /bin/sleep 15
    async: 45
    poll: 5
  ```

  [参考](http://ansible-tran.readthedocs.io/en/latest/docs/playbooks_async.html)