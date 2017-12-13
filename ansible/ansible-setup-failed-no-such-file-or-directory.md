#### 表象

![](/assets/setup_error.png)

#### 原因

原因是系统文件损坏：

![](/assets/file_system_currupt.png)

#### 定位思路

排查部分文件损坏的脚本：将一下文件复制到异常节点任意目录，在root用户下直接执行python xxx.py：

![](/assets/check_removable_files.py)![](/assets/check_discard_granularity.py)

