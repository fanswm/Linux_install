+ unexpected inconsistency RUN fsck ma...系统不能启动
> 插入livecd,进入命令行（假设grub在/dev/sda11）
> fsck -y sda11
> or: `fsck -t ext4 /dev/sda11`
reboot,ok
