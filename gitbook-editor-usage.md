[gitbook的基本用法非常简单](http://www.chengweiyang.cn/gitbook/basic-usage/README.html)

#### 本工程包含如下内容，大家一起来补充

* Ansible和DMK常见错误
* Linux和Ansible使用技巧
* DMK使用指南

---

##### 1. 下载GitBook.Editor并安装在本地

##### 2. 克隆本工程到本地

> git@code-xa.huawei.com:devops/book.git

##### 3. 新建分支，使用GitBook Editor编写并提交

##### 4. File -&gt; Open -&gt; 选择刚克隆岛本地的工程目录

![](/assets/gitbook_editor_open.png)

##### 5. 在对应的分类下，创建新的article

![](/assets/gitbook_editor_new_artical.png)

##### 6. 编辑完成后，记着点击左上角的 “save” 按钮来保存数据

##### 7. 打开Git GUI,Branch->Create 来创建自己的分支；Branch->Checkout 来切换到自己的分支，如下图：

![](/assets/gitbook_editor_new_branch1.png)

![](/assets/gitbook_editor_new_branch2.png)

##### 8. 提交更改,将代码推送至远端

![](/assets/gitbook_editor_git_push.png)

##### 9. 提MR，请求合入代码，链接如下：

>  http://code.huawei.com/devops/book/merge_requests

MR创建完成后，最新的gitbook将会自动部署在下面的server中，这时你可以上去检查自己修改的内容是否OK。

> http://10.154.68.45:5000       #不对外公布

待MR合入后，最新的代码将会自动部署到：

> http://10.154.68.45:4000       #正式环境

---

##### GitBook Editor使用特别方便，注意一些坑

**1. 最大的坑**

即使本地的分支切到了你的分支，但是Open打开后，会默认是master分支。所以：

> 每次一定要在修改前**查看右上角显示的分支是不是你的分支**

**2. 新建artical一定要用**`英文`**，不然你回后悔的**

gitbook serve起在Linux上，但是Linux对中文支持不好，所以可以先使用英文，然后再编辑修改。

**3. 必须相关文件**

**3.1 README.md**

典型的， 是介绍。它可以自动的被加到最终的summary中。

**3.2 SUMMARY.md是书籍的目录结构**

![](/assets/gitbook_editor_usage.png)

