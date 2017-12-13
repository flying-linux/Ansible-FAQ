### DMK 适配 Euler OS


#### 1. 使用源码安装ansible

* 碰到问题1：root下可以，但在dmk（普通）用户下，ansible命令无法使用

 * 解决：ansible命令所属用户和组均为root，所以需要修改权限为755。
   * `chmod o+rx /usr/bin/ansible*`


* 碰到问题2：ansible命令能找到，但是查看版本或者使用就会报错`No module named 'pkg_resources'`
 * 定位过程：查看root用户和dmk用户下，Python加载的系统环境路径有什么区别？
 ```
 python 
 import sys
 sys.path
 ```
 * 解决：`chmod -R o+rx /usr/lib/python2.7/site-packages`
 
#### 2. 安装ruby

* 碰到问题1：rails起不来
* 解决：重新编译ruby，指定路径为`/opt/ruby/ruby`



 
