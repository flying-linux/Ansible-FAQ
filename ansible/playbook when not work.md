#### 问题：
定义的when判断一直不起作用

#### 表象：


```
- name: install dcm agent
  hosts: dcm-agent
  remote_user: "{{ remote_user }}"
  roles:
    - { role: common }
    - { role: consul-agent }
    - { role: test, when: "'{{test_flag}}' == 'true'" }
```

#### 原因：

ansible将布尔变量转化成了`True`、`False`

#### 解决：


```
- name: install dcm agent
  hosts: dcm-agent
  remote_user: "{{ remote_user }}"
  roles:
    - { role: common }
    - { role: consul-agent }
    - { role: test, when: "'{{test_flag}}' == 'True'" }
```


OR:

``` 

- name: install dcm agent
  hosts: dcm-agent
  remote_user: "{{ remote_user }}"
  roles:
    - { role: common }
    - { role: consul-agent }
    - { role: test, when: "{{test_flag}} == true" }
```