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
  + `useradd admin -d /home/admin`
  + `passwd admin`
  + `chown -R admin:admin /home/admin`
  + `chown -R admin:admin /var/run/tor`
  
## 测试：
+ 启动Tor成功之后，可以输入`netstat -lnt`查看本机的网络状态，
> tcp     0     0     127.0.0.1:9050      0.0.0.0:*      LISTEN  

> [参考][1]
> [参考2][2]

[1]: https://linux.cn/article-3566-1.html "tor安装参考"
[2]: http://blog.csdn.net/smiler_sun/article/details/71124082 "tor参考2"
