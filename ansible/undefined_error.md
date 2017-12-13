#### 问题：

* one or more undefined variables : 'xxxx' has no attribute 'xxxx'


* UndefinedError: 'xxxx' is undefined

#### 表象：


![](/assets/undefined_error1.png)


![](/assets/undefined_error2.png)


####原因：

参数未定义。

####解决：

找到对应的变量并进行赋值定义。

```

提示：该变量可能存在于：

DMK portal可见的配置，如：公共配置、服务自己的配置文件 ;

DMK portal不可见的配置，如：default_all 、特性开关(DT_all, HEC_all,TLF_all, ...等);

```







