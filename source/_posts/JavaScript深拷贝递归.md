---
title: JavaScript浅拷贝和深拷贝递归
date: 2017-3-11 13:09:04
tags: [JavaScript,面向对象程序设计]
---
浅拷贝的结果是两个引用指向同一个对象，即同一片内存区域。

### 浅拷贝

``` javascript
 var Ethan = {name: 'xia.weihua', height: '177cm', girlfriend: {name: 'leftHand'}};  // Just a joke, never mind.
 var Jack = Ethan;
 
 Jack.height = '165cm';
 
 console.log(Ethan); 
 console.log(Jack);
```
```
 { name: 'xia.weihua',
   height: '165cm',     // I'm not
   girlfriend: { name: 'leftHand' } }
 { name: 'xia.weihua',   
   height: '165cm',
   girlfriend: { name: 'leftHand' } }   
 
```
<!-- more -->

### 深拷贝
深拷贝的结果是两个引用指向不同对象，即不同内存区域。实现深拷贝需要递归
``` javascript 
var Ethan = {name: 'xia.weihua', height: '177cm', girlfriend: {name: 'leftHand'}};
var Jack;

function deepCopy(obj) {
    var temp = obj.constructor === Array ? [] : {};
    if (typeof obj !== 'object') {
        return obj;
    } else {
        for (var i in obj) {
            temp[i] = deepCopy(obj[i]);
        }
    }
    return temp;
}

Jack = deepCopy(Ethan);
Jack.name = 'Jack Neo';
Jack.height = '165cm';
Jack.girlfriend.name = 'rightHand';


console.log(Ethan);
console.log(Jack);
```
```
{ name: 'xia.weihua',
  height: '177cm',
  girlfriend: { name: 'leftHand' } }
{ name: 'Jack Neo',
  height: '165cm',
  girlfriend: { name: 'rightHand' } }
```
版权声明：本文为博主原创文章，转载时注明，谢谢。
