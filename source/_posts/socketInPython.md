---
title: 套接字socket在Python中的用法测试
date: 2016-11-10 13:09:04
tags: [Python2.7, socket, 多线程]
---
本部分介绍 socket — Low-level networking interface   偏底层的接口
区别于 socketserver  — A framework for network   框架
## 从计算机网络开始
OSI七层协议：物理层，数据链路层，网络层，运输层，会话层，表示层，应用层
TCP/IP的体系结构：网络接口层，网际层IP，运输层（TCP或UDP），应用层（TELNET,FTP,SMTP）
五层协议体系结构：物理层，数据链路层，网络层，运输层，应用层
套接字=IP地址 + 端口 + TCP协议或UDP协议  进程与进程之间的网络通信方式或者本机不同进程通过文件系统之间的通信方式

套接字家族选择（socket family）
基于文件的套接字：单机套接字，使用文件系统作基础，AF_UNIX或者AF_LOCAL
基于网路的套接字：不同主机进程之间通信的套接字，AF_INET和AP_INET6 （AF_INET是用于IPV4,而AF_INET6是用于IPV6）
套接字传输数据类型选择（type)
TCP协议：通信前需要建立连接，连接是可靠的。使用的套接字类型是SOCK_STREAM
UDP协议：无需连接就能通信，速度快，可靠性不高。传输用户数据报格式UDP的数据。使用的套接字类型是SOCK_DGRAM

由于套接字创建以后归属与一个进程。因此，在操作系统课本中有进程的状态与转换（王道计算机操作系统第28页）
一个服务端进程的状态如下：创建—>就绪—>运行—>阻塞（一直while循环等待客户端）—>运行（收到请求链接并响应 三次握手）->终止（关闭服务停止运行）
<!-- more -->
### 套接字超时注意事项
TCP协议位于传输层，提供可靠的字节流服务Byte Stream Service。由于在用TCP协议，因此要三次握手建立连接，四次挥手关闭连接。
如果由于三次握手是需要在一定的时间范围内完成的动作，如果没有完成就超时了。或者三次握手之后，其他通信操作没有及时完成就会出现超时。此时就要做出相应的操作，例如重新执行动作，否则就会失败。
套接字对象可以是以下三种模式之一：阻塞，非阻塞或超时。默认情况下，套接字创建后处于阻塞模式，但可以通过调用 setdefaulttimeout() 来更改。
在 阻塞模式 中，操作阻塞直到完成或系统返回错误（例如连接超时）。
在 非阻塞模式 中，如果无法立即完成操作，那么操作将失败（错误是与系统相关的错误）：来自 select 的函数可用于知道套接字何时可用于读取或写入。
在 超时模式 中，如果无法在为套接字指定的超时（它们引发 timeout 异常）或系统返回错误时无法完成操作，则操作将失败。

<!-- more -->

### 使用TCP协议套接字用Python2.7实现单线程聊天程序和多线程程序
``` python
#仅支持IPV4
#server.py
#!/usr/bin/python 2.7
# -*- coding: utf-8 -*-
# @Time    : 2017/5/18 22:52
# @Author  : Ethan Sha
# @File    : server.py
# @Software: PyCharm
import socket

HOST = '127.0.0.1'
PORT = 21567
BUFSIZ = 1024
ADDR = (HOST, PORT)

tcp_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
tcp_socket.bind(ADDR)
tcp_socket.listen(5)

while True:
    print "waiting for connection..."
    tcp_connection, tcp_address = tcp_socket.accept()
    print 'connected from:', tcp_address
    while True:
        data = tcp_connection.recv(BUFSIZ)
        if not data:
            break
        print 'Jack:' + data
        data = raw_input('send message> ')
        tcp_connection.sendall(data)
    tcp_connection.close()
tcp_socket.close()

```

``` python
#client.py
#!/usr/bin/python 2.7
# -*- coding: utf-8 -*-
# @Time    : 2017/5/18 22:52
# @Author  : Ethan Sha
# @File    : client.py
# @Software: PyCharm
import socket

HOST = 'localhost'
PORT = 21567
BUFSIZ = 1024
ADDR = (HOST, PORT)

tcp_socket_client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
tcp_socket_client.connect(ADDR)

while True:
    data = raw_input('send message> ')
    tcp_socket_client.send(data)
    data = tcp_socket_client.recv(BUFSIZ)
    if not data:
        break
    print 'Ethan:' + data
tcp_socket_client.close()
```
先打开server,再打开client。之后client输入你好，server再输入你也好啊。如此反复即可。要实现类似QQ的聊天。需要多线程或多进程。
``` bash
# server
waiting for connection...
connected from: ('127.0.0.1', 63922)
Jack:你好
send message> 你也好啊
```
``` bash
# client
send message> 你好
Ethan:你也好啊
send message> 
```

### 多线程聊天程序
四个线程，server和client都有两个线程，第一个线程是发送消息，第二个线程是接收消息。
``` python
# server.py
#!/usr/bin/python 2.7
# -*- coding: utf-8 -*-
# @Time    : 2017/5/18 22:52
# @Author  : Ethan Sha
# @File    : server.py
# @Software: PyCharm

import socket
import thread

HOST = '127.0.0.1'
PORT = 21567
BUFSIZ = 1024
ADDR = (HOST, PORT)

tcp_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
tcp_socket.bind(ADDR)
tcp_socket.listen(5)

print "waiting for connection..."
tcp_connection, tcp_address = tcp_socket.accept()
print 'connected from:', tcp_address


def send_msg_thread():
    while True:
        msg = raw_input()
        tcp_connection.sendall(msg)


def recv_msg_thread():
    while True:
        data = tcp_connection.recv(BUFSIZ)
        if not data:
            break
        print 'Jack:' + data

try:
    thread.start_new_thread(send_msg_thread, ())
    thread.start_new_thread(recv_msg_thread, ())
except:
    print "Error: unable to start thread"
while 1:
    pass

```
``` python
# client.py 
#!/usr/bin/python 2.7
# -*- coding: utf-8 -*-
# @Time    : 2017/5/18 22:52
# @Author  : Ethan Sha
# @File    : server.py
# @Software: PyCharm

import socket
import thread

HOST = 'localhost'
PORT = 21567
BUFSIZ = 1024
ADDR = (HOST, PORT)

tcp_socket_client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
tcp_socket_client.connect(ADDR)


def send_msg_thread():
    while True:
        msg = raw_input()
        tcp_socket_client.send(msg)


def recv_msg_thread():
    while True:
        data = tcp_socket_client.recv(BUFSIZ)
        if not data:
            break
        print 'Ethan:' + data

try:
    thread.start_new_thread(send_msg_thread, ())
    thread.start_new_thread(recv_msg_thread, ())
except:
    print "Error: unable to start thread"
# tcp_socket_client.close()
while 1:
    pass

```

``` python
# server
waiting for connection...
connected from: ('127.0.0.1', 59918)
你好， 多线程聊天程序了解一下~~
Jack:兄贵真皮，程序写的溜溜的...
```

``` python
# client
Ethan:你好， 多线程聊天程序了解一下~~
兄贵真皮，程序写的溜溜的...
```

版权所有 转载注明。Thank you




