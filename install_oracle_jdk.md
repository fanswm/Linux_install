## 把openjdk替换成oracle jdk:


	从oracle官网下载：jdk-8u111-linux-x64.tar.gz


	



	myusername@dns:~$ which java


	/usr/bin/java


	myusername@dns:~$ ll /usr/bin/java


	lrwxrwxrwx 1 root root 22 11月 12 20:09 /usr/bin/java -> /etc/alternatives/java


	myusername@dns:~$ ll /etc/alternatives/java


	lrwxrwxrwx 1 root root 46 11月 12 20:08 /etc/alternatives/java -> /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java


	



	root@dns:/home/myusername/tmp# java -version


	openjdk version "1.8.0_111"


	OpenJDK Runtime Environment (build 1.8.0_111-8u111-b14-2-b14)


	OpenJDK 64-Bit Server VM (build 25.111-b14, mixed mode)


	



	



	$ tar xvf jdk-8u121-linux-i586.tar.gz


	$ mv jdk1.8.0_121 /usr/lib/jvm/


	$ ls -la /usr/lib/jvm/


	$ cd /usr/lib/jvm/jdk1.8.0_111/


	$ update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8.0_121/bin/java 1


	$ update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.8.0_121/bin/javac 1


	$ update-alternatives --set java /usr/lib/jvm/jdk1.8.0_121/bin/java


	$ update-alternatives --set javac /usr/lib/jvm/jdk1.8.0_121/bin/javac


	$ java -version   #查看是否正确链接到java jdk版本


	安装之前的指向：


	/usr/bin/java -> /etc/alternatives/java -> /usr/bin/java java /usr/lib/jvm/jdk-8-openjdk-amd64/bin/java


	$ java -version


	:


	openjdk version "1.8.0_111"


	OpenJDK Runtime Environment (build 1.8.0_111-8u111-b14-2-b14)


	OpenJDK 64-Bit Server VM (build 25.111-b14, mixed mode)


	



	安装之后的指向：


	/usr/bin/java -> /etc/alternatives/java -> /usr/bin/java java /usr/lib/jvm/jdk1.8.0_31/bin/java


	$ java -version


	:


	java version "1.8.0_111"


	Java(TM) SE Runtime Environment (build 1.8.0_111-b14)


	Java HotSpot(TM) 64-Bit Server VM (build 25.111-b14, mixed mode)


	



	test:


	HelloWorld.java:


	public class HelloWorld {


	     public static void main(String[] args) {


	                 System.out.println("Hello World!");


	        }


	 }


	$ javac HelloWorld.java


	$ java HelloWorld      
