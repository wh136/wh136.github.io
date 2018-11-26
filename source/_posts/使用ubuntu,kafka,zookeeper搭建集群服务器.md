---
title: 使用ubuntu,kafka,zookeeper搭建集群服务器
date: 2017-2-1 13:09:04
tags: [集群服务器,分布式,Vmware虚拟机,Linux]
---
本文将粗略描述一台电脑或者多台电脑搭建集群服务器。以此提供分布式发布订阅消息系统，大数据hadoop，简单的机器学习等多种服务需要的运行环境。
环境与工具：Windows 10、vmware 14 Pro、ubuntu 16LTS、kafka_2.11-0.11.0.0、zookeeper-3.4.5、xshell5
配置：8G内存、256G固态、 1T机械、 GTX 850、Intel i5-CPU
kafka：一种高吞吐量的分布式发布订阅消息系统
zookeeper：分布式应用程序协调服务，是Hadoop和Hbase的重要组件，提供的功能包括：配置维护、域名服务、分布式同步、组服务等。
## 安装ubuntu16，JDK，kafka，zookeeper并配置vmware 14 pro
在虚拟机中安装ubuntu16. [下载ubuntu](https://www.ubuntu.com/download/desktop)
安装完毕后，进入登录界面，此时登录的是安装时注册的用户。
接着创建root用户,再登入root
``` bash
wh136@ubuntu:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password:
wh136@ubuntu:~$ su
root@ubuntu:/#
```
<!-- more -->
并配置网络，使ubuntu有独立IP地址，也能连接互联网。方便安装JDK,kafka,zookeeper
配置网络
![配置网络](https://onedrive.gimhoy.com/1drv/aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBbmhUd09YVkZoTzRoV1c1N2lkS1dlbUpyOVNB.jpg)
![配置网络](https://onedrive.gimhoy.com/1drv/aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBbmhUd09YVkZoTzRoV2dWZ1Y5TktSQUZ3UDFJ.jpg)
![网关](https://onedrive.gimhoy.com/1drv/aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBbmhUd09YVkZoTzRoV09NdTFtQ2VYNzEycTNp.jpg)

### 互相ping测试网络
![windows ping ubuntu](https://onedrive.gimhoy.com/1drv/aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBbmhUd09YVkZoTzRoV1l1UlZTWkhhUml4QmNq.jpg)
![ubuntu ping windows](https://onedrive.gimhoy.com/1drv/aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBbmhUd09YVkZoTzRoV2ZtbnpNb0NNbFNTU2tv.jpg)
网络互通。

然后再回到ubunutu安装SSH服务，最后使用xshell5连接到ubunutu
``` bash
wh136@ubuntu:~$ sudo apt-get install openssh-server    //安装SSH服务
wh136@ubuntu:~$ sudo ps -e |grep ssh        //检查SSH是否启动 有sshd则启动了
wh136@ubuntu:~$ sudo service ssh start      //启动SSH服务
```
![xshell连接ubuntu](https://onedrive.gimhoy.com/1drv/aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBbmhUd09YVkZoTzRoV25kZVB5SEdmcVJydjdC.jpg)
这样就搭建了第一台服务器，你想搭几台都可以，只要电脑硬件足够好。给每个虚拟机分配足够多的硬件资源就行。
注意！在使用完毕后，先把虚拟机中的服务器关闭，再关闭电脑。不能随意关闭，否则有可能造成文件丢失，虚拟机中的系统出现故障。

### 安装JDK
通过ppa(源) 方式安装JDK.(可以通过 apt-get upgrade 方式方便获得jdk的升级)
``` bash
root@ubuntu:/# sudo add-apt-repository ppa:webupd8team/java         //添加ppa 添加仓库源：
root@ubuntu:/# sudo apt-get update                                  //更新软件包列表
root@ubuntu:/# sudo apt-get install oracle-java8-installer          //安装Oracle-java-installer 
root@ubuntu:/# sudo update-java-alternatives -s java-8-oracle       //设置系统默认jdk
root@ubuntu:/# java -version                                        //测试jdk是否安装成功
root@ubuntu:/# javac -version
```
### 安装kafka,zookeeper（配置比较麻烦，暂时放一放）
``` bash
root@ubuntu:/# cd /usr/local
root@ubuntu:/usr/local# wget https://archive.apache.org/dist/zookeeper/zookeeper-3.4.5/zookeeper-3.4.5.tar.gz   //注意zookeeper的版本号。后续有些操作会有差别。
root@ubuntu:/usr/local# wget http://archive.apache.org/dist/kafka/0.11.0.0/kafka_2.11-0.11.0.0.tgz
root@ubuntu:/usr/local# ls
bin  etc  games  include  kafka_2.11-0.11.0.0.tgz  lib  man  sbin  share  src   zookeeper-3.4.5.tar.gz
root@ubuntu:/usr/local# tar -xzvf kafka_2.11-1.0.0.tgz   //解压
root@ubuntu:/usr/local# tar -xzvf zookeeper-3.4.5.tar.gz
root@ubuntu:/usr/local# cd conf                          //配置
root@ubuntu:/usr/local# cp zoo_sample.cfg zoo.cfg
..... //配置待续
```
版权声明：本文为博主原创文章，转载时注明，谢谢。



