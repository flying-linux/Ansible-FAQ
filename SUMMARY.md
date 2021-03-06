# Summary

* [效率提升](README.md)
* [Ansible Error](ansible/README.md)
  * [playbook常用问题定位方法](ansible/ansible-playbook-debug.md)
  * [Authentication Failure](ansible/section1.md)
  * [Incorrect become password](ansible/section2.md)
  * [SSH Error: Permission denied\(public key, password\)](ansible/section3.md)
  * [checksum failed](ansible/checksum.md)
  * [Connection reset by peer](ansible/sftp_closed.md)
  * [global name 'errors' is not defined](ansible/global-name-is-not-defined.md)
  * [Failed to find handler to unarchive](ansible/unarchive-failed.md)
  * [Ansible任务卡死，场景收集](ansible/ansible-playbook-stuck.md)
  * [getpwdnam name not found](ansible/getpwdnam-name-not-found.md)
  * [Fail regardless of when](ansible/fail-regardless-of-when.md)
  * [playbook任务耗时巨大](ansible/playbook task consume long time.md)
  * [ssh connection closed waiting for a privilege escalation password prompt](ansible/waiting-for-a-privilege-escalation-password-prompt.md)
  * [playbook when not work](ansible/playbook when not work.md)
  * [ansible setup failed: No such file or directory](ansible/ansible-setup-failed-no-such-file-or-directory.md)
  * [Shared connection closed](ansible/shared-connection-closed.md)
  * [SSH ERROR: data could not be sent to the remote host. Make sure this host can be reached over ssh](ansible/data-could-not-be-sent-to-the-remote-host.md)
  * [host key fingerprint check](ansible/host-key-fingerprint-check.md)
  * [ssh connection error while waiting for sudo password prompt](ansible/ssh-connection-error-while-waiting-for-sudo.md)
  * [cannot create directory permission denied](ansible/cannot-create-directory-permission-denied.md)
  * [LVS安装SSH卡死问题验证](ansible/lvs-agent-hang.md)
  * [import xxx failed](ansible/import-xxx-failed.md)
  * [命令无法执行，抛出command not found错误](ansible/throw_invailed_message.md)
  * [can not open file xxx command](ansible/can-not-open-file-xxx-command.md)
  * [Undefined variables](ansible/undefined_error.md)
  * [密码过期，任务卡死](ansible/password_expired_hang.md)
  * [卡死或Write failed: Broken Pipe](ansible/write-failed-broken-pipe.md)
  * [Xshell能连接但DMK连接失败](ansible/xshell-can-connect-but-ansible-can't.md)
* [DMK Error](dmk/README.md)
  * [验证码刷不出来](dmk/section1.md)
  * [软件包同步失败](dmk/section2.md)
  * [获取第三方软件列表](dmk/get_3rd_list.md)
  * [DMK界面不符合预期](dmk/dmk-portal-problem.md)
  * [上传包失败](dmk/upload_package_failed.md)
  * [升级至2.1.1版本后数据同步问题](dmk/2.1.1version_error.md)
  * [单节点DMK，服务无法自动拉起](dmk/start_process.md)
  * [全局配置文件不存在](dmk/globle_undefined_error.md)
* [Knowledge](Knowledge/README.md)
  * [Linux mount](Knowledge/mount.md)
  * [Linux screen](Knowledge/linux-screen-command.md)
  * [Linux rsync](Knowledge/linux-rsync.md)
  * [Linux watch](Knowledge/linux-watch.md)
  * [Linux sar](Knowledge/linux-sar.md)
  * [软、硬链接](Knowledge/hard-soft-link.md)
  * [GitBook Editor安装插件](Knowledge/gitbook-editor-install-plugin.md)
  * [nginx.conf配置文件](Knowledge/nginx.md)
  * [理解正向和反向代理](Knowledge/proxy.md)
  * [了解文件系统](Knowledge/linux-ext3-journal.md)
  * [PgUp PgDn History](Knowledge/pgup-pgdn-history.md)
* [DMK Guide](Guide/README.md)
  * [DMK适配、安装、升级](Guide/dmk.md)
  * [Ansible Config Set](Guide/ansible-config-set.md)
  * [修改Ansible配置，提升性能](Guide/serviceansibleconfigset.md)
  * [SSH连通性验证](Guide/troubleshoot-ssh-problems.md)
  * [SSH跳板机](Guide/ssh-springboard.md)
  * [Repoman对接及问题排查](Guide/test.md)
  * [包类型、账号创建说明](Guide/verify-package-team.md)
  * [克隆生成DMK主备节点](Guide/clone-dmk-server.md)
  * [DMK账号过期特性修改](Guide/user_pwd_update_trigger.md)
  * [修改浮动IP](Guide/modify-floatip.md)
  * [解锁、修改sysadmin密码](Guide/modify_sysadmin_passwd.md)
  * [多Region功能指导](Guide/multi_region.md)
  * [DMK对接OpsAssistant](Guide/dmk-opsassistant.md)
  * [DMK配置生效优先级](Guide/dmk_config_priority.md)
  * [Account验证使用指南](dmk/validate_user_guide.md)
  * [DMK的API调用指导](Guide/dmk_api_call.md)
  * [DMK后台修改playbook](Guide/modify_playbook_backend.md)
  * [DMK Vault使用指南](Guide/dmk-vault.md)
  * [DMK跳板机使用指南](Guide/dmk_proxy_guide.md)
  * [Euler的DMK上Playbook语法检查](Guide/euler_dmk_playbook_syntax_check.md)
  * [DMK任务的保存和配置查找](Guide/job-store-and-configs.md)
  * [Ansible使用su提权](Guide/switch-sudo-to-su.md)
  * [主机仓库 使用指导](Guide/hosts.md)
* [Wiki](Wiki/README.md)
  * [Gitbook CI启动](Wiki/screen_gitbook_jenkins.md)
  * [系统健康检查](Wiki/health-check-report.md)
  * [rsync系统盘IO 100%](Wiki/rsync-system-io-high.md)
  * [Ubuntu 14.04安装ROR](Wiki/ubuntu-1404-install-ruby-on-rails.md)
  * [Ubuntu安装GitBook](Wiki/ubuntu-install-gitbook.md)
  * [Book CI](Wiki/ubuntu-book-cd.md)
  * [趟坑后的简易CI过程](Wiki/easyjenkinsbookci.md)
  * [欧拉LVM](Wiki/redhatiplvm.md)
  * [SSH登录和交互](Wiki/sshstudy.md)
  * [DMK欧拉适配](Wiki/dmk-euler-install.md)
  * [Ubuntu Use Zsh](Wiki/ubuntu-use-zsh.md)
  * [Gitbook CI启动](Wiki/screen_gitbook_jenkins.md)
  * [GitBook Editor 使用指南](gitbook-editor-usage.md)
* [Ansible 1.9 VS 2.2](Guide/README.md)
  * [roles](Guide/roles.md)
  * [playbook](1.9VS2.2/playbook.md)
  * [Unable to find .. in expected paths](1.9VS2.2/unable-to-find--in-expected-paths.md)

