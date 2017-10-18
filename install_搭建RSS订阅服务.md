## 安装docker
+ `sudo curl -sSL https://get.daocloud.io/docker | sh`

## 安装postgres
+ `sudo docker run -d --name ttrssdb nornagon/postgres`

## 安装RSS订阅
+ `sudo docker run -d --link ttrssdb:db -p 80:80 -e SELF_URL_PATH=http://172.17.0.1 fischerman/docker-ttrss`
> 前一个“80”，是docker内部端口；冒号后面的是映射到主机的端口；“172.17.0.1”是docker的ip。
