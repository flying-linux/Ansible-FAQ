### DMK部署脚本下配置生效的优先级

| 部署配置 | 解释 |
| --- | --- |
| group_vars/all/all | UI上显示并人工配置 |
| group_vars/service_all/default_all | 各服务部署中的默认/隐藏配置（每次job都会生效） |
| group_var/service_all/{CTC}_all，类似还有HEC_all, DT_all | 局点特性开关配置文件（根据全局配置g_current_region.location值加载；匹配上就加载，匹配不上就不加载) |
| global_all（不在服务部署脚本） | 全局公共配置 |

### 优先级

##### all &gt; global\_all &gt; default_all &gt; CTC_all(类似还有HEC_all, DT_all)



