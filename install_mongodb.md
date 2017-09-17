## 安装mongodb:
+ `sudo apt-get update && sudo apt-get upgrade -y`
+ `sudo apt-get install mongodb`

## 测试mongodb安装:
+ `mkdir /home/fanswm/mongodata`

## 用以下命令启动mongod:
+ `mongod --dbpath /home/fanswm/mongodata`

> 这时mongod已经启动，重新打开一个终端, 键入mongo进入交互程序：
+ `mongo`
> show dbs

> mongodb安装到此为止
