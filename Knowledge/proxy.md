![](/assets/proxy.jpg)


* 正向代理中，proxy和client同属一个LAN，对server透明；
* 反向代理中，proxy和server同属一个LAN，对client透明。

实际上proxy在两种代理中做的事都是代为收发请求和响应，
不过从结构上来看正好左右互换了下，所以把后出现的那种代理方式叫成了反向代理。


----


![](/assets/proxy_people.jpg)


* 一个是代理(v)客户端，为客户端收发请求，使真实客户端对服务器不可见。
* 一个是代理(v)服务器，为服务器收发请求，使真实服务器对客户端不可见。

因为服务对象和自身角色不同，所以刚好是相反的。

