## 安装：
+ `sudo add-apt-repository ppa:webupd8team/tor-browser`
+ `sudo apt-get update`
+ `sudo apt-get install tor-browser`
+ `sudo apt-get install tor`

## 卸载：
+ `sudo apt-get remove tor-browser`
+ `rm -r ~/.tor-browser-en`

## 启动：
+ 添加用户：
  + `useradd toradmin -d /home/admin`
  + `passwd toradmin`
  + `chown -R toradmin:toradmin /home/admin`
  + `chown -R toradmin:toradmin /var/run/tor`
  + `su toradmin`
  + tor-browser-en.sh
  
## 测试：
+ 启动Tor成功之后，可以输入`netstat -lnt`查看本机的网络状态，
> tcp     0     0     127.0.0.1:9050      0.0.0.0:*      LISTEN  

## 代理配置
> 现在要使该服务器成为一个TOR代理，使得其他主机可以使用该服务器的TOR代理，需要进行如下配置:
+ `vim /etc/tor/torrc` 修改SOCK5代理端口，添加以下语句:

> SOCKSPort 9050 # Default: Bind to localhost:9050 for local connections.  
SOCKSPort 0.0.0.0:9150 # Bind to this address:port too.  

+ 重新运行TOR，查看网络状态，新打开监听端口9150
> tcp     0     0    127.0.0.1:9050     0.0.0.0:*       LISTEN             
tcp     0     0    0.0.0.0:9150          0.0.0.0:*       LISTEN 

> 因为TOR提供的SOCK5代理没有用户密码验证。所以我们需要配置防火墙，修改iptables来指定允许的IP连接该端口。或者直接修改Tor配置文件，只允许指定的IP访问TOR代理接口，在torrc文件末尾添加以下语句。
SOCKSPolicy accept   45.32.24.178    
SOCKSPolicy reject *  
#SOCKSPolicy accept 192.168.0.0/16  

> 使用其他主机测试该代理，在一台VPS上配置firefox浏览器socks5代理为该服务器的9150端口，然后通过浏览器百度自己的ip，或者访问https://check.torproject.org/?lang=zh_CN，可以发现该浏览器的流量走的是tor网络。如果想要使整个主机流量走TOR网络，可以配合proxyfier等全局代理工具使用。

> [ubuntu 14.04如何安装tor-browser][1]

> [如何在linux环境下搭建Tor代理服务器][2]

[1]: https://linux.cn/article-3566-1.html "tor安装参考"
[2]: http://blog.csdn.net/smiler_sun/article/details/71124082 "tor参考2"
