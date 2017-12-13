#### nginx.conf配置文件

Nginx配置文件主要分成四部分：

main（全局设置）、server（主机设置）、upstream（上游服务器设置，主要为反向代理、负载均衡相关配置）和 location（URL匹配特定位置后的设置），每部分包含若干个指令。

* main设置为全局设置的指令，将影响其它所有部分的设置；
* server部分的指令主要用于指定虚拟主机域名、IP和端口；
* upstream的指令用于设置一系列的后端服务器，设置反向代理及后端服务器的负载均衡；
* location部分用于匹配网页位置（比如，根目录“/”,“/images”,等等）。

他们之间的关系式：server继承main，location继承server；upstream既不会继承指令也不会被继承。它有自己的特殊指令，不需要在其他地方的应用。

