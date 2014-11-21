teamtalk
========

菜鸟编译teamtalk
1.CENTOS 6.X系统准备

2.下载jdk  jdk-7u67-linux-x64.rpm 放到jdk目录下

3.Setup.sh格式转转成unix ，vi setup.sh    :set ff=unix

4.安装gcc

yum -y install gcc

yum -y install gcc-c++

yum install make

 

-- 或者

yum groupinstall "Development Tools"

 

-- 或者

yum install gcc gcc-c++ kernel-devel

5.安装MVN

首先从官网上 http://maven.apache.org/ 下载最新版Maven。我用的是apache-maven-3.0.4-bin.tar.gz。将下载后的文件拷贝到 /usr/local/目录下。

1、执行 tar -zxvf apache-maven-3.0.4-bin.tar.gz 命令解压文件

2、解压后会生成apache-maven-3.0.4目录，删除apache-maven-3.0.4-bin.tar.gz压缩包文件

3、执行 ln -s apache-maven-3.0.4 apache-maven（为Maven做一个软链接，方便以后升级）

4、执行 vi /etc/profile 文件，插入如下内容

         export M2_HOME=/usr/local/apache-maven

         PATH=$PATH:$JAVA_HOME/bin:$M2_HOME/bin

 

         export PATH USER LOGNAME MAIL HOSTNAME HISTSIZE ...

 

5、保存并退出VI编辑器，执行 source /etc/profile 命令使改动生效

 

6、执行 mvn -v 命令，如出现如下内容表示安装配置成功

 

         [root@xg /]# mvn -v                                                                                                       

         Apache Maven 3.0.4 (r1232337; 2012-01-17 16:44:56+0800)                                       

         Maven home: /usr/local/apache-maven                                                                             

         Java version: 1.6.0_33, vendor: Sun Microsystems Inc.                                                    

         Java home: /usr/local/jdk1.6.0_33/jre                                                                             

         Default locale: zh_CN, platform encoding: UTF-8                                                               

         OS name: "linux", version: "2.6.32-279.2.1.el6.x86_64", arch: "amd64", family: "unix"   

 

zmalloc.h:50:31: 错误：jemalloc/jemalloc.h：没有那个文件或目录

zmalloc.h:55:2: 错误：#error "Newer version of jemalloc required"

>>解决

make的时候加上 MALLOC=libc 参数

make PREFIX=/data/apps/redis2.6.14 MALLOC=libc install

6.更改IP

###1.纯公司内网  的机器内网ip为：192.168.231.129

**login_server:**

ClientListenIP=192.168.231.129

ClientPort=8008

MsgServerListenIP=192.168.231.129

MsgServerPort=8100

**msg_server:**

ListenIP=192.168.231.129

ListenPort=8200

HttpListenIP=192.168.231.129

HttpListenPort=8300

ConcurrentDBConnCnt=2

DBServerIP1=192.168.231.129

DBServerPort1=11000

DBServerIP2=192.168.231.129

DBServerPort2=11000

LoginServerIP1=192.168.231.129

LoginServerPort1=8100

RouteServerIP1=192.168.231.129

RouteServerPort1=8400

FileServerIP1=192.168.231.129

FileServerPort1=8500

IpAddr1=192.168.231.129

IpAddr2=192.168.231.129

MaxConnCnt=100000

**route_server:**

ListenIP=192.168.231.129

ListenMsgPort=8400

**msfs_server:**

ListenIP=192.168.231.129

ListenPort=8600BaseDir=./tmp

FileCnt=0

FilesPerDir=30000

GetThreadCount=32

PostThreadCount=1

**file_server:**

Address=192.168.231.129

ListenPort=8500

TaskTimeout=60

7.进入ttautodeploy 执行 ./setup.sh install

 

      

 

8.打开后台管理 http://127.0.0.1



9.进入mysql 更改密码加密

update IMUsers set pwd=md5('123456') ;

10.关闭centos防火墙

       关闭虚拟机防火墙：

关闭命令：  service iptables stop

永久关闭防火墙：chkconfig iptables off

 

两个命令同时运行，运行完成后查看防火墙关闭状态

service iptables status

11.用win客户端登陆



用户名 C  密码123456

 

运行截图



