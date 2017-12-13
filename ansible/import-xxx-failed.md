#### 问题：

#### **''import sitecustomize' failed; use -v for traceback， 或 import xxx failed**

#### 表象：

![](/assets/import_xxx_failed.png)

#### 原因：

**python环境异常，需定位无法import的模块**


#### 解决：

* 如果该模块不是python2.6.9必须的，则删除该模块；

* 如果是python2.6.9标准模块，需要从新安装python或从DMK正常节点复制一份；



