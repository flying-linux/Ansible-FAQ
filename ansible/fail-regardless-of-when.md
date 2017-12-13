#### 问题： 
任务日志显示执行成功，但是提示信息Fail 


#### 表象： 
![](/assets/fail_msg.png) 

#### 原因： 
Ansible的task可以指定name，为可选。 

如果不填写，默认会在执行过程中显示`模块+参数`的，所以会出现无论when条件是否判断，都会输出`fail msg="secforce failed"` 

#### 解决： 
加上`name` 

#### 备注 
**通过本地测试，发现细心点会发现区别的：** 

![](/assets/fail_local_test.png)
