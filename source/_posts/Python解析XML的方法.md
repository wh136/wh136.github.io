---
title: Python解析XML的方法，用于简单对象访问协议（SOAP）
date: 2016-9-16 13:09:04
tags: [Python2.7,XML,WebService]
---

### 预备知识
Python解析XML三种方法及优缺点
1.SAX (simple API for XML )     需要用户实现回调函数（handler）
2.DOM(Document Object Model)    DOM需要将XML数据映射到内存中的树，比较慢，比较耗内存
3.ElementTree(元素树)            轻量级的DOM 代码可用性好，速度快，消耗内存少

<!-- more -->
### 使用ElementTree解析XML
country_data.xml
```XML
<?xml version="1.0"?>
<data>
    <country name="Liechtenstein">
        <rank>1</rank>
        <year>2008</year>
        <gdppc>141100</gdppc>
        <neighbor name="Austria" direction="E"/>
        <neighbor name="Switzerland" direction="W"/>
    </country>
    <country name="Singapore">
        <rank>4</rank>
        <year>2011</year>
        <gdppc>59900</gdppc>
        <neighbor name="Malaysia" direction="N"/>
    </country>
    <country name="Panama">
        <rank>68</rank>
        <year>2011</year>
        <gdppc>13600</gdppc>
        <neighbor name="Costa Rica" direction="W"/>
        <neighbor name="Colombia" direction="E"/>
    </country>
</data>
```
增加，删除，查询，修改等基本功能Python都能够提供支持。下面有简单举例，具体操作API文档有详细例子。
为实现简单对象访问协议SOAP相关业务，应能够读取XML文件，根据业务要求，配合整个系统，修改XML，或发送或保存为XML文件。
完成实际的需求即可。
```Python
#!/usr/bin/python 2.7
# -*- coding: utf-8 -*-
import xml.etree.ElementTree as ET
tree = ET.parse('country_data.xml')
root_1 = tree.getroot()
print tostring(root_1)  //根元素data
```
版权声明：本文为博主原创文章，转载时注明，谢谢。