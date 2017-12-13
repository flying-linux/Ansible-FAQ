####  Jumper特性
* DMK Jumper特性用于解决跨网络部署的难题。

* DMK服务器位于OM区域，与public区域网络隔离，无法直接部署，可通过proxy间接部署public网络区域的节点。

![](/assets/proxy_dmk.png)

#### 1.1 前提条件
Jumper模式需要一跳转节点（Bastion），该节点有以下限制：

1. 与DMK和目标节点网络可达，ssh相通；
2. 该节点需要预先创建部署所用账号，允许并打开该节点的PubkeyAuthentication、PasswordAuthentication和AllowTcpForwarding；
3. 该节点以及目标节点sftp可用，如果不可用请在ansible.cfg文件中添加以下配置：scp_if_ssh=True；
4. 该节点存在nc命令：which nc；

#### 1.2 使用
##### 1.2.1 创建Jumper
如果需要通过Jumper部署目标主机，需要在DMK预先创建代理节点。

以运维账号登录DMK，进入“Hosts”界面下的“SSH Jumper”页签，点击“Add Jumper”。

![](/assets/add_jumper.png)  

##### 1.2.2 Proxy参数
![](/assets/create_proxy.png)

Proxy创建后，会尝试进行以下操作：

1. DMK服务器与跳转机建立互信，因此必须确保所填信息准确，否则会创建失败；
2. 创建ssh_config文件和jumper_arg_config（对应于options参数）文件，部署时，DMK负责将这两个文件复制到playbook执行目录(/pkg_repo/data/jobs/{job_id})下面，供服务组脚本使用；
 
##### playbook执行目录
![](/assets/jumper_playbook.png) 

##### ssh_config文件,其中 IdentityFile: 私钥文件，用于DMK连接跳转机 
![](/assets/jumper_file.png)

##### 目前仅仅ELB使用此功能
![](/assets/deploy_with_jumper.png) 
  
