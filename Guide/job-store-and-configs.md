### 任务（包含日志、配置）保存目录
以DMK为例，开始执行任务到结束，会保留到多个目录
* **工作目录**：/pkg_repo/data/jobs/{job_id}
* 执行`结束`，**归档目录**：/pkg_repo/jobs/{job_id}
* 执行`成功`，还要再保存到**latest_configs**：/pkg_repo/data/latest_configs/DMK/{job_id}


### 配置查询目录流程
**工作目录 -> 归档目录 -> latest_configs**