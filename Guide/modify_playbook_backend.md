#### DMK后台修改playbook
##### DMK后台存放playbook的目录有2个：
1. /pkg_repo/playbook
2. /pkg_repo/playbook_sync_store/playbook


#### 需要修改playbook，应该在哪个目录呢？
* 一定优先在同步目录`/pkg_repo/playbook_sync_store/playbook/{{service}}/{{version}}`查找并修改。

* 若没有找到，则在`/pkg_repo/playbook/{{service}}/{{version}}`查找并修改。

----

据统计playbook目录下的目录和文件个数超过140万个（文件不大，小文件特别多），HA占用CPU持续100%，所以新增专门同步目录。

> [参考](http://3ms.huawei.com/hi/blog/608373_2285211.html)