---
title: 简单对象访问协议Simple Object Access Protocol(SOAP)
date: 2016-10-16 13:09:04
tags: [XML,HTTP协议,WebService]

---

### 预备知识
Simple Object Access Protocol是应用程序交换消息数据的一种协议，使用在web服务(Web Service),SOAP是其简写，
由于非常容易与Service-oriented architecture(SOA)产生歧义，在2003年SOAP这种缩写被废止了。

一个简单对象访问协议(Simple Object Access Protocol)的消息是一个普通的XML文档，并包含以下元素。
1.一个信封元素Envelope element用于定义一个XML文档为简单对象访问协议(Simple Object Access Protocol)的消息。
2.一个头元素header element包含头信息
3.一个体元素body element包含呼叫和应答信息
4.一个过错元素fault element包含问题和状态信息
<!-- more -->
简单对象访问协议Simple Object Access Protocol消息的结构
```XML
<?xml version="1.0"?>

<soap:Envelope
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">

<soap:Header>
...
</soap:Header>

<soap:Body>
...
  <soap:Fault>
  ...
  </soap:Fault>
</soap:Body>

</soap:Envelope>
```
信封元素Envelope element包含Namespace命名空间和encodingStyle Attribute编码格式属性
```XML
<?xml version="1.0"?>

<soap:Envelope
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">
  ...
  Message information goes here
  ...
</soap:Envelope>
```

该协议的消息结构具体信息：[简单对象访问协议](https://www.w3schools.com/xml/xml_soap.asp)

在了解完该协议下消息的结构后，需要交换消息，可以使用应用层协议来传输消息，例如SMTP、HTTP、HTTPS。
下面以HTTP协议为例，介绍向服务器发送请求股票(IBM股票)价格SOAP消息，服务器返回股票价格SOAP消息。
### HTTP协议(Hypertext Transfer Protocol超文本传输协议)
HTTP协议是基于TCP/IP协议族进行消息文本传输的协议，一个HTTP客户端连接一个HTTP服务器需要用[TCP协议](https://zh.wikipedia.org/wiki/%E4%BC%A0%E8%BE%93%E6%8E%A7%E5%88%B6%E5%8D%8F%E8%AE%AE)（传输控制协议Transmission Control Protocol）
在建立连接之后，客户端可以向服务器发送HTTP请求消息。
```
POST /item HTTP/1.1
Host: 189.123.255.239
Content-Type: text/plain
Content-Length: 200
```
服务器收到请求并且该请求是正确的格式，向客户端发动响应，该响应包含一个状态码表明请求收到。
```
200 OK
Content-Type: text/plain
Content-Length: 200
```
### 简单对象访问协议绑定(SOAP Binding)
通过简单对象访问协议绑定可以进行数据交换，该绑定的原理是使用传输协议（transport protocol）交换SOAP消息。
大多数简单对象访问协议绑定（SOAP Binding）的实现模块提供了对HTTP、SMTP协议的绑定
HTTP协议是同步的，并且被广泛的应用于生活中。一个SOAP HTTP请求限定了至少两个HTTP头（HTTP headers）Content-Type 和 Content-Length
SMTP协议是异步的，是特殊情况下才用的特效解药。
Java对SOAP的实现提供了一个对JMS协议（Java Messaging System）的绑定。
Python对SOAP的实现，针对web服务(WebService)有soaplib库，但是在2011年官网停止对该库更新。并且转向另外一个库rpclib

### Content-Type和Content-Length
SOAP请求和响应的Content-Type头规定了MIME type，消息的MIME type和字符编码被用于规定XML体的请求、响应。
```
Content-Type: MIMEType; charset=character-encoding
```
例子
```
POST /item HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8
```
SOAP请求和响应的Content-Length规定了请求、响应体中的字节数。
```
Content-Length: bytes
```
例子
```
POST /item HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8
Content-Length: 250
```
### 正式开始我们的主菜！股票价格SOAP消息
一个含有股票名（IBM）的请求价格消息如下所示，在发送到服务端后，我们将收到SOAP股票价格消息，这个功能的命名空间定义在"http://www.example.org/stock".
SOAP请求
```
POST /InStock HTTP/1.1
Host: www.example.org
Content-Type: application/soap+xml; charset=utf-8
Content-Length: nnn

<?xml version="1.0"?>

<soap:Envelope
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">

<soap:Body xmlns:m="http://www.example.org/stock">
  <m:GetStockPrice>
    <m:StockName>IBM</m:StockName>
  </m:GetStockPrice>
</soap:Body>

</soap:Envelope>
```
SOAP响应
```
HTTP/1.1 200 OK
Content-Type: application/soap+xml; charset=utf-8
Content-Length: nnn

<?xml version="1.0"?>

<soap:Envelope
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">

<soap:Body xmlns:m="http://www.example.org/stock">
  <m:GetStockPriceResponse>
    <m:Price>34.5</m:Price>
  </m:GetStockPriceResponse>
</soap:Body>

</soap:Envelope>
```
版权声明：本文为博主原创文章，转载时注明，谢谢。