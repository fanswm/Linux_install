+ 查看版本：
> + uname -a 
> + cat /proc/version （Linux查看当前操作系统版本信息） 
> + cat /etc/issue 或cat /etc/redhat-release（Linux查看版本当前操作系统发行版信息） 
> + cat /proc/cpuinfo （Linux查看cpu相关信息，包括型号、主频、内核信息等） 
> + getconf LONG_BIT （Linux查看版本说明当前CPU运行在32bit模式下， 但不代表CPU不支持64bit） 
> + lsb_release -a

## CentOS查看系统版本：
+ `cat /proc/version`
+ `uname -a`
+ `uname -r`

## 查看Linux版本：
+ 列出所有版本信息：
	+ `lsb_release -a`
	+ `cat /etc/issue`
	+ `cat /etc/redhat-release`
+ 查看系统是64位还是32位：
	+ `getconf LONG_BIT`	
	+ `getconf WORD_BIT`
	+ `file /bin/ls`


