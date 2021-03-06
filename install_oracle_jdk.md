## 把openjdk替换成oracle jdk:

## 从oracle官网下载：jdk-8u111-linux-x64.tar.gz

## 查看机器上的java安装在哪儿：
+ `myusername@dns:~$ which java`
> /usr/bin/java

## 查看`/usr/bin/java`指向哪里：
+ `myusername@dns:~$ ll /usr/bin/java`
> lrwxrwxrwx 1 root root 22 11月 12 20:09 /usr/bin/java -> /etc/alternatives/java

## 查看`/etc/alternatives/java`指向哪里：
+ `myusername@dns:~$ ll /etc/alternatives/java`
> lrwxrwxrwx 1 root root 46 11月 12 20:08 /etc/alternatives/java -> /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java


> 请把以下的`myusername`替换成你自己的名字：
+ `root@dns:/home/myusername/tmp# java -version`
> openjdk version "1.8.0_111"
OpenJDK Runtime Environment (build 1.8.0_111-8u111-b14-2-b14)
OpenJDK 64-Bit Server VM (build 25.111-b14, mixed mode)

## install:
+ `tar xvf jdk-8u121-linux-i586.tar.gz`
+ `mv jdk1.8.0_121 /usr/lib/jvm/`
+ `ls -la /usr/lib/jvm/`
+ `cd /usr/lib/jvm/jdk1.8.0_111/`
+ `update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8.0_121/bin/java 1`
+ `update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.8.0_121/bin/javac 1`
+ `update-alternatives --set java /usr/lib/jvm/jdk1.8.0_121/bin/java`
+ `update-alternatives --set javac /usr/lib/jvm/jdk1.8.0_121/bin/javac`
+ `java -version`

##查看是否正确链接到java jdk版本

> 安装之前的指向：
`/usr/bin/java -> /etc/alternatives/java -> /usr/bin/java java /usr/lib/jvm/jdk-8-openjdk-amd64/bin/java`

+ `java -version`

> openjdk version "1.8.0_111"
OpenJDK Runtime Environment (build 1.8.0_111-8u111-b14-2-b14)
OpenJDK 64-Bit Server VM (build 25.111-b14, mixed mode)

> 安装之后的指向：
`/usr/bin/java -> /etc/alternatives/java -> /usr/bin/java java /usr/lib/jvm/jdk1.8.0_31/bin/java`

+ `java -version`
> java version "1.8.0_111"
Java(TM) SE Runtime Environment (build 1.8.0_111-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.111-b14, mixed mode)

## test: HelloWorld.java:
```
public class HelloWorld {
	public static void main(String[] args) {
		 System.out.println("Hello World!");
	}
}
```
## 编译
+ `javac HelloWorld.java`

## 运行
+ `java HelloWorld`   


# 如果之前没有安装java或openjdk：
+ 下载[jdk-9_linux-x64_bin.tar.gz][1]
+ `tar -zxvf jdk-9_linux-x64_bin.tar.gz`
+ `sudo su`
+ `mv jdk-9 /usr/lib/jvm`
+ `cd /usr/lib/jvm`
+ `update-alternatives --install /usr/bin/java java /usr/lib/jvm/bin/java 1`
+ `update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/bin/javac 1`
+ `ln -s /usr/bin/javac /usr/lib/jvm/javac`
> 不知有没有用
+ `update-alternatives --set java /usr/lib/jvm/bin/java`
+ `update-alternatives --set javac /usr/lib/jvm/bin/javac`
+ `java --version`
> 再测试.


[1]: http://www.oracle.com/technetwork/java/javase/downloads/jdk9-downloads-3848520.html "jdk download"
