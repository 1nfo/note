#install R and Java
---
##R
R在win和osx下都好说，直接下载双击解决。linux呢，本来也不麻烦，直接：
>sudo get-apt install r-base-core

就好了。不过打开一看，是3.0.2版本，最新的是3.2.0.（星期六, 09. 五月 2015 02:56上午 ）。于是，只好去cran下载。方法有很多，下载deb是其中一种，也是我唯一尝试成功的一种。

去china的镜像下找到ubuntu的相应版本（我的是14.04 ，好像没有直接对应的），选的是trusty（ubuntu 12.02，如果没记错的话。。。）
注意选3.2.0最新的，包括了r-base-core r-commend r-base 等（好像这三个就够了，还有安装顺序要对）
下载好了后双击解决。。。之后输入R 就是3.2.0了
---
Java
首先，这里install Java，不是要直接用Java。R里面需要rJava包，这个包需要Java。

1. 首先从oracle的官网上下载java的jdk，注意系统类别和系统位数。
1. mv到/usr/lib/java中去

>tar -zxfv *yourdownloadFILE* 

这样程序有了，还要配置一下环境  （
>sudo gedit /etc/profile

内容如下

	export JAVA_HOME=/usr/lib/jdk/jdk1.8.0_45
	export JRE_HOME=/usr/lib/jdk/jdk1.8.0_45/jre
	export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
	export CLASSPATH=$CLASSPATH:.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib

对于R 还要配置

>sudo R CMD javaconf JAVA=\usr\lib\jdk\...\java

还有javac，javah，jar 都要添加

最后要在R中安装，注意权限
>sudo R
>......some words about R
>install.packages('rJava')