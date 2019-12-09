---
title: JS运算符
date: 2019-12-09 13:50:49
tags:
 - JS细节知识点
 - JS

photos:
 - https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/js-1.jpg
---

本文旨在彻底弄清在平时并不常用或是使用时容易出现歧义、模糊的js运算符，对于平时常用的运算符不做探讨研究

<!-- more -->

## <font color=#4fc08d>\#</font>JS逻辑运算符  ||  &&

### 逻辑与、短路与( && ) / 逻辑或、短路或( || )

**作用：**
        
`a && b` 左右两侧同为true时返回true，其中一侧为false时返回false。

`a || b` 左右两侧其中一侧为true时返回true，同为false时返回false。
    
**延申：**
        
 `&&` 在执行左侧为false后，右侧表达式不再执行

`||` 在执行左侧为true时，右侧表达式不再执行
    
```javascript
let a = 1;
let b = 1;
console.log(false && function(){a = 2; return 'abc123'}());
console.log(true || function(){b = 2; return 'abc123'}());
console.log(a);
console.log(b);
//结果：a = 1; b = 1;
```
    
相对短路与&& - 按位与 / 短路或||& - 按位或
    
```javascript
let a = 1;
let b = 1;
console.log(false & function(){a = 2; return 'abc123'}());
console.log(false | function(){b = 2; return 'abc123'}());
console.log(a);
console.log(b);
//结果：a = 2; b = 2;
```

按位与/按位或，由于存在强制类型转换，在判断数字时会执行强制类型转换，使用位运算，故不做逻辑运算使用。

<br/>

---
## <font color=#4fc08d>\#</font>JS位运算符 & | ~ ^ << >> >>>符

### 按位与( & ) / 按位或( | )

**作用：**

`a & b` 用于对两个二进制操作数逐位进行比较，两侧同为true时返回true，见下表所示的换算表结果。

{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/js%E6%93%8D%E4%BD%9C%E7%AC%A6/and.png %}

`a | b` 用于对两个二进制操作数逐位进行比较，一侧为true时返回true，，见下表所示的换算表结果。

{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/js%E6%93%8D%E4%BD%9C%E7%AC%A6/or.png %}

### 按位非( ~ )

**作用：**

` ~a ` 用于对一个二进制操作数逐位进行取反操作。

运算步骤 ( ~1 )：
- 把`1`数转换为 32 位的二进制整数 = `0000 ··· 0001`;
- 按位取反`1111 ··· 1110`;
- 最高位即为符号位 ( 1为负数 )，将除符号位之外的其他数字取反 = `1000 ··· 0001`;
- 末位加1取其补码 = `1000 ··· 0010`;
- 转换为二进制 = `-2`;

**延申：**

计算机计算减法的实现原理是，将减法变为加一个负数，而负数则是以补码的形式存储在计算机中;

实现原理为：
如想详细了解计算机运算规则需要了解两个概念：

反码：将数字的二级制数按位取反得其反码;

补码：将反码`+1`为其补码;

如：
- `-1`的反码为，`+1`的二级制数`00000001`按位取反`11111110`
- 将`-1`的反码`+1`的出`-1`的补码为`11111111`

假设计算机存储八位二级制数字，最高可存储`11111111`十进制也就是`255`，如果255再加1，二级制数运算结果为`100000000`依据计算机计算原则，高位溢出，最终的结果为`00000000`;

依据此项特性，采用的是补码的方式存储数字,最高位为其符号位，可将减法转换为加一个负数;

如：

`1 + (-1)`的二进制计算为`00000001 + 11111111`,最终结果为`00000000`十进制结果为`0`符合十进制运算规则;

### 移位运算符 ( >> << >>> )

**待写**


---
## <font color=#4fc08d>\#</font>JS类型运算符  typeof instanceof

**待写**


