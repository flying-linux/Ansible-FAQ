## 健康检查脚本

**脚本描述：SuSe系统健康检查，包含如下内容：
**

```
# 1. 内存，磁盘，load超过阈值，告警              (阈值可配置)
# 2. 系统进程，异常告警                         (进程可配置)
# 3. 密码过期时间，若到达提示修改时间，告警       (用户可配置)
# 4. IO，网络的检查
```

---

### 各健康项的判断点：

#### 1. 内存使用率不能超99%

* 依据：内存使用率来判断，使用率超过`99%`，则认为异常。
* 问题：为什么设置阈值为99%？
* 理由：Linux设计思想，`内存不用白不用`，因此它`尽可能`的cache和buffer一些数据，以方便下次使用，但实际上这些内存也是可以立刻拿来使用的。
* 结论：`可用内存 == free memory + buffers + cached` == `total-used`


#### 2. 磁盘全监控，使用率不能超过80%

* 早发现，早清理
* 计划监控`重要磁盘`, 其他磁盘出现异常也应该通知管理员，所以改为`所有磁盘全监控`。
* 当然，也可设置为90%，可配置

#### 3. load使用最近15分钟内的平均值，不能超过机器CPU核数

* [理解load averages](http://3ms.huawei.com/hi/blog/608373_2438709.html?h=h)
* CPU核数设置为load的阈值             
  ```
  load_threshold=$(grep 'model name' /proc/cpuinfo | wc -l)
  ```


#### 4. 磁盘IO使用率不能超过80%

* 此处可能为多磁盘，即使是100%，因为磁盘的并发能力，所以磁盘使用未必就到了瓶颈。
* 早发现，早处理，分析是瞬时增高，还是其他什么原因引起（会另写一篇文章，分析IO高的定位思路）。

#### 5. 网络，发送和接收包不能有错误

![](/assets/network_error_check.png)

#### 6. 用户密码即将过期，提醒修改

* [理解密码策略保存文件](https://www.cyberciti.biz/faq/understanding-etcshadow-file/)
* [查看某个用户密码时间策略](http://www.thegeekstuff.com/2009/04/chage-linux-password-expiration-and-aging/)

---

附：[自己写的健康检查Suse系统的Shell脚本](http://code.huawei.com/snippets/618)

