1. 下载jdk8

　　[官网][http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html]

　　> 选择对应jdk版本下载。（Tips：可在Windows下载完成后，通过FTP或者SSH到发送到Linux上）

2. `sudo su`

3. 在usr目录下建立java安装目录
    ```
    cd /usr
    mkdir java
    ```

4. 将jdk-8u60-linux-x64.tar.gz拷贝到java目录下
    `cp /mnt/hgfs/linux/jdk-8u60-linux-x64.tar.gz /usr/java/`

5. 解压jdk到当前目录,得到文件夹 jdk1.8.0_*　　(注意：下载不同版本的JDK目录名不同！)
    `tar -zxvf jdk-8u60-linux-x64.tar.gz`

6. 安装完毕为他建立一个链接以节省目录长度
    `ln -s /usr/java/jdk1.8.0_60/ /usr/jdk`

7. 编辑配置文件，配置环境变量
    `vim /etc/profile`
    > 在文本的末尾添加如下内容：
    ```
        JAVA_HOME=/usr/jdk
        CLASSPATH=$JAVA_HOME/lib/
        PATH=$PATH:$JAVA_HOME/bin
        export PATH JAVA_HOME CLASSPATH
    ```

8. 重启机器或执行命令
    `source /etc/profile`

9. 查看安装情况
    `java -version`

> ps:可能出现的错误信息：
　　bash: ./java: cannot execute binary file
　出现这个错误的原因可能是在32位的操作系统上安装了64位的jdk，
　　1、查看jdk版本和Linux版本位数是否一致。
　　2、查看你安装的Ubuntu是32位还是64位系统：
sudo uname -m
　　附：i686    //表示是32位
　　     x86_64  // 表示是64位
简书链接：http://www.jianshu.com/p/cb3ceb066ea8

20171023:
## 安装前：
java -version
openjdk version "1.8.0_151"
OpenJDK Runtime Environment (build 1.8.0_151-b12)
OpenJDK 64-Bit Server VM (build 25.151-b12, mixed mode)

## 安装后：
> fanswm:
`alias java='/usr/jdk/bin/java'
`

