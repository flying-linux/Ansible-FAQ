#### Ubuntu安装使用Zsh（Oh-My-Zsh 可以让终端及美观又实用）

##### 安装zsh：

1. sudo apt-get install zsh，安装zsh
2. zsh --version，确认是否安装成功
3. sudo chsh -s $(which zsh)，设置zsh为默认shell
4. reboot，注销重新登录
5. 登录上后，确认是否切换成功，echo $SHELL

##### 安装oh-my-zsh
1. Windows上登陆github，按下图红圈下载压缩包：
```
访问 https://github.com/robbyrussell/oh-my-zsh --> Clone or download --> DownloadZip 
```
2. 在Ubuntu机器上创建目录：  
```
mkdir .oh-my-zsh
```
3. 上传下载的oh-my-zsh-master.zip，然后xftp把解压的文件拷贝到上面的目录里：
![](/assets/oh_my_zsh.PNG)
4. 在主目录下创建.zshrc文件
```
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```

##### 修改主题
>zsh的皮肤列表：https://github.com/robbyrussell/oh-my-zsh/wiki/themes

1. vi ~/.zshrc
```
ZSH_THEME="选中的主题名字"
```
2. source ~/.zshrc

3. 自己找了个主题安装[powerlevel9k](https://github.com/bhilburn/powerlevel9k/)
   * 下载源码解压到`~/.oh-my-zsh/custom/themes/powerlevel9k`目录
   * vi ~/.zshrc
   
```
ZSH_THEME="powerlevel9k/powerlevel9k"
...
POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(time dir vcs)
POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status rbenv)
POWERLEVEL9K_STATUS_VERBOSE=false
POWERLEVEL9K_SHORTEN_STRATEGY="truncate_middle"
POWERLEVEL9K_SHORTEN_DIR_LENGTH=3

POWERLEVEL9K_OS_ICON_BACKGROUND="white"
POWERLEVEL9K_OS_ICON_FOREGROUND="blue"
POWERLEVEL9K_DIR_HOME_FOREGROUND="white"
POWERLEVEL9K_DIR_HOME_SUBFOLDER_FOREGROUND="white"
POWERLEVEL9K_DIR_DEFAULT_FOREGROUND="white"
```
   * source ~/.zshrc

##### 使用插件