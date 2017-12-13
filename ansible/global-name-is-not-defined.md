#### 问题：NameError: global name 'errors' is not defined

#### 表现：

```
TASK: [jdk | download jdk file] *********************************************** 
fatal: [oncf_host] => Traceback (most recent call last):
  File "/usr/lib64/python2.6/site-packages/ansible/runner/__init__.py", line 582, in _executor
    exec_rc = self._executor_internal(host, new_stdin)
  File "/usr/lib64/python2.6/site-packages/ansible/runner/__init__.py", line 785, in _executor_internal
    return self._executor_internal_inner(host, self.module_args, inject, port, complex_args=complex_args)
  File "/usr/lib64/python2.6/site-packages/ansible/runner/__init__.py", line 1032, in _executor_internal_inner
    result = handler.run(conn, tmp, module_name, module_args, inject, complex_args)
  File "/usr/lib64/python2.6/site-packages/ansible/runner/action_plugins/copy.py", line 165, in run
    local_checksum = utils.checksum(source_full)
  File "/usr/lib64/python2.6/site-packages/ansible/utils/hashing.py", line 66, in secure_hash
    raise errors.AnsibleError("error while accessing the file %s, error was: %s" % (filename, e))
NameError: global name 'errors' is not defined
```

#### 原因：

3rd下文件所属用户和用户组不对

#### 解决：

```
chown dmk:dmk -R /pkg_repo/3rd/*
```