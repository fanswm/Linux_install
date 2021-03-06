# at pi:

## 下载leanote.tar.gz
+ `mv leanote.tar.gz ~/`
+ `tar -zxvf leanote.tar.gz`

## 安装mongodb:
> https://github.com/myusername/Linux_install/blob/master/install_mongodb.md

> https://github.com/myusername/Linux_install/blob/master/install_golang.md

## 导入初始数据:
> leanote初始数据存放在 `/home/user1/leanote/mongodb_backup/leanote_install_data`中。

+ 打开终端， 输入以下命令导入数据。注意mongodb v2 与 v3 版本导入数据的区别：
> mongodb v2 导入数据命令:
  + `$>mongorestore -h localhost -d leanote --directoryperdb /home/user1/leanote/mongodb_backup/leanote_install_data/`

> mongodb v3 导入数据命令:
  + `$> mongorestore -h localhost -d leanote --dir /home/user1/leanote/mongodb_backup/leanote_install_data/`

> 现在在mongodb中已经新建了leanote数据库, 可用命令查看下leanote有多少张"表":
+ `mongo`

> + > 查看数据库
> `> show dbs`

> leanote 0.203125GB
> local   0.078125GB

> + 切换到leanote
`> use leanote`
> switched to db leanote

> + 查看表
`> show collections`

## 初始数据的users表中已有2个用户:
+ user1 username: admin, password: abc123 (管理员, 只有该用户才有权管理后台, 请及时修改密码)
+ user2 username: demo@leanote.com, password: demo@leanote.com (仅供体验使用)

> 端口9001

## 配置leanote:
> leanote的配置存储在文件 `conf/app.conf` 中。
> 请务必修改`app.secret`一项, 在若干个随机位置处，将字符修改成一个其他的值, 否则会有安全隐患!
> 其它的配置可暂时保持不变, 若需要配置数据库信息, 请参照 leanote问题汇总。

## 运行leanote:
> 注意: 在此之前请确保mongodb已在运行!

+ 新开一个窗口, 运行:
+ `cd /home/myusername/leanote/bin`
+ `chmod u+x ./run.sh`
+ `run.sh`

+ 最后出现以下信息证明运行成功:
> ...
TRACE 2013/06/06 15:01:27 watcher.go:72: Watching: /home/life/leanote/bin/src/github.com/leanote/leanote/conf/routes
Go to /@tests to run the tests.
Listening on :9000...

> 恭喜你, 打开浏览器输入: http://localhost:9000 体验leanote吧!

# at pi:(官方教程)

## 安装go语言
leanote是基于golang开发的，解释器必然是不可少的 
life 的推荐是使用 go语言的二进制包。版本在1.3.1以上。 
然而，golang官方没有给出arm的二进制包。ubuntu最新的官方源中的版本为1.2.1。 
所以只好自己编译。。
1 . 2 下载golang源码
  1. wget https://storage.googleapis.com/golang/go1.4.2.src.tar.gz -P /usr/local/src
1 . 3 安装
1.3.1 解压
  1. cd /usr/local/src && tar zxvf go1.4.2.src.tar.gz
1.3.2 设置编译参数
  1. export GOROOT=/usr/local/src/go
  2. export GOOS=linux
  3. export GOARCH=arm
  4. export GOARM=7
GOROOT = golang目录 
GOOS = 编译的目标系统 PS:比如 linux 、 windows 、 freeBSD 等等 
GOARCH = 编译的目标平台 PS: 368 、 amd64 、 arm 
GOARM = 表示使用的浮点运算协处理器版本号，只对arm平台有用，可选值有5，6，7。如果是在目标平台上编译源代码，这个值可以不设置，它会自动判断需要使用哪一个版本。
1.3.3 编译
  1. cd go/src && ./make.bash
src子目录中，主要有all.bash和make.bash两个脚本.两者的区别在于all.bash在编译完成后还会执行一些测试套件.
2 . 安装mongodb
同上 天杀的 官方也没有提供 arm 的二进制包。万幸 apt 的版本能用。
2.1 apt安装mongodb
  1. apt-get install git mongodb sysv-rc-conf -y
2.2 开机启动
  1. sysv-rc-conf mongodb on
3 . 安装 leanote
3.1 创建GO目录
  1. mdkir /usr/local/gopackage
  2. ln -s /usr/local/src/go /usr/local/go
3.2 下载最新开发版本
  1. cd /usr/local/src && wget https://github.com/leanote/leanote-all/archive/master.zip
  2. unzip master.zip
  3. mv leanote-all-master/* /usr/local/gopackage/
3.3 添加 环境变量
  1. cat << EOF >> /etc/profile
  2. export GOROOT=/usr/local/go
  3. export GOPATH=/usr/local/gopackage
  4. export PATH=\$PATH:\$GOPATH/bin:\$GOROOT/bin
  5. EOF
3.4 安装必要包
  1. apt-get install -y git-core mercurial openssh-server openssh-client
  2. go get github.com/revel/cmd/revel
  3. go get github.com/leanote/leanote/app
3.5 导入数据库文件
  1. mongorestore -h localhost -d leanote --directoryperdb /usr/local/gopackage/src/github.com/leanote/leanote/mongodb_backup/leanote_install_data/
3.6 配置leanote
  1. vim /usr/local/gopackage/src/github.com/leanote/leanote/conf/app.conf
主要修改
  ●  http.port=8080
  ●  site.url=http://192.168.1.1:8080
  ●  db.username	mongoadmin
  ●  db.password	mongo+简
4 开机运行 leanote
  1. vim /etc/rc.local
  2. exit前添加
  3. mongod --dbpath=/var/lib/mongodb &
  4. export GOROOT=/usr/local/go
  5. export GOPATH=/usr/local/gopackage
  6. export PATH=$PATH:$GOPATH/bin:$GOROOT/bin
  7. revel run github.com/leanote/leanote &

# at Win10:
$ go version
go version go1.4.2 windows/386

$ mongo --version
MongoDB shell version:2.6.8

mongorestore  -h localhost -d leanote  --directoryperdb D:\Go\src\github.com\leanote\leanote\mongodb_backup\leanote_install_data

leanote的配置存储在文件 D:\Go\src\github.com\leanote\leanote\conf/app.conf 中。

# You Must Change It !! About Security!!
app.secret=V85ZzBeTnzpsHyjQX4zukbQ8qqtju9y2aDM55VWxAH9Qop19poekx3xkcDVvrD0y #

to:
# You Must Change It !! About Security!!
app.secret=V85ZzaeTnzpsHyjQX4zukbQ8qitju9y2aDM55VWxXH9Qop19p1ekx3xkcDVvrD0y #


$ go install D:\Go\src\github.com\revel\cmd\revel
$ cd d:\Go
$ go install github.com\revel\cmd\revel
$ revel run github.com\\leanote\\leanote

user1 username: admin, password: abc123 (管理员, 只有该用户可以管理后台)
user2 username: demo@leanote.com, password: demo@leanote.com (仅共体验使用)

# at pi:

## 添加服务脚本:

$ sudo vim /etc/init.d/leanote
append:

```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          /home/myusername/leanote/bin	by:myusername
# Required-Start:    $remote_fs $network
# Required-Stop:     $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Aria2 Downloader
### END INIT INFO
case "$1" in
start)
    echo -n "Starting leanote \n"
    sudo -u myusername /home/myusername/leanote/bin/run.sh &
;;
stop)
    echo -n "Shutting down leanote \n"
    killall /home/myusername/leanote/bin/leanote-linux-arm
;;
restart)
    killall /home/myusername/leanote/bin/leanote-linux-arm
    sudo -u myusername /home/myusername/leanote/bin/run.sh &
esac
exit
```

+ 启动：
`sudo /etc/init.d/leanote start`
+ 停止：
`sudo /etc/init.d/leanote stop`


# at win10:
`cd ~/git/`
`git clone https://github.com/leanote/leanote.git`
`mongorestore -h localhost -d leanote --directoryperdb /home/user1/leanote/mongodb_backup/leanote_install_data/`

# 安卓端登录：
点击下方：使用自定义服务器：http://mydomain.ddns.net:端口号

