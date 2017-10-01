+ 添加 PPA 源的命令为：
> `sudo add-apt-repository ppa:user/ppa-name`

> 例如，要添加一个用户名为 eugenesan 到 java 源中，则命令为
> `sudo add-apt-repository ppa:eugenesan/java`

+ 添加好更新一下： `sudo apt-get update`

+ 删除命令格式则为：
> `sudo add-apt-repository -r ppa:user/ppa-name`

> 如`sudo add-apt-repository -r ppa:eugenesan/java`
> + 然后进入 /etc/apt/sources.list.d 目录，将相应 ppa 源的保存文件删除。
