## 查看开机启动项
+ `清理开机启动项`

## 停止项目
> 例如
+ `sudo systemctl stop bluetooth.service`
+ `sudo systemctl disable bluetooth.service`

## 通过下面命令确定是否操作成功
+ ` systemctl status bluetooth.service`

## 阻止该进程在任何情况下开机启动
> 停用的服务进程仍然能够被另外一个服务进程启动。如果你真的想在任何情况下系统启动时都不启动该进程，无需卸载该它，只需要把它掩盖起来就可以阻止该进程在任何情况下开机启动。

+ `sudo systemctl mask bluetooth.service`

## 卸载该程序
> 一旦你对禁用该进程启动而没有出现负面作用感到满意，你也可以选择卸载该程序。

## 获得如下服务列表
+ `systemctl list-unit-files --type=service`
> 你不能启用或禁用静态服务，因为静态服务被其他的进程所依赖，并不意味着它们自己运行.

## 哪些服务能够禁止
