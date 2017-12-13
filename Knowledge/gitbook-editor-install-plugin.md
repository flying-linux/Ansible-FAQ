#### 1. 修改book.json

```
{
    "title": "效率提升",
    "description": "Ansible、DMK FAQ, Knowledge and Wiki",
    "plugins": [
         "theme-comscore",
         "splitter",
         "prism", 
         "-highlight",
         "toggle-chapters"
    ]
}
```

#### 2. gitbook install

![](/assets/gitbook_install.png)




#### 遇到一个问题
![](/assets/gitbook_cli.png)


**根据提示，执行如下2个命令：**
```
sudo npm uninstall -g gitbook
sudo npm install -g gitbook-cli
```