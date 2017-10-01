## 无法获得锁 /var/lib/dpkg/lock - open (11: 资源暂时不可用)

> 解决办法如下：

+ 终端输入 ps  aux ，列出进程。找到含有apt-get的进程，直接sudo kill PID。

+ 强制解锁,命令
> + `sudo rm /var/cache/apt/archives/lock`
> + `sudo rm /var/lib/dpkg/lock`
