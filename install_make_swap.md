### 查看swap分区
`free -h`

### 创建一个swap分区
`dd if=/dev/zero of=/doiido/swap bs=1024 count=8388608`
> count的计算公式： count=SIZE*1024(SIZE以MB为单位)
> 8GB

### 格式化新建的分区
`mkswap /doiido/swap`

### 把新建的分区变为swap分区
`swapon /doiido/swap`
> 关闭swap分区的命令为：`swapoff /doiido/swap`

### 查看swap分区的大小
`free -h`

### 开机自动挂载swap分区
```
sudo vim /etc/fstab
# /doiido/swap	swap	swap	defaults	0	0
```
