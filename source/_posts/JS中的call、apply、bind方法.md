---
title: JS中的call、apply、bind方法
date: 2019-08-06 09:16:29
tags:
 - JS细节知识点
 - JS

photos:
 - https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/js-1.jpg
---

JS中call、apply、bind方法的使用及区别。

<!-- more -->

### <font color=#4fc08d>\#</font>call、apply、bind用法

```js
function NumberUtil() {}
NumberUtil.prototype = {
    number: 0,
    say: function() {
      console.log("My default number is " + this.number);
    },
    sum: function() {
      console.log("Sum is " + (arguments[0] + arguments[1]));
    }
}
  
var num = new NumberUtil;
num.say();

```
声明一个构造器对象，并绑定say函数与sum函数，其中say函数为打印当前对象的number属性，sum函数为获取传入数组的和;
```js
var numberObj = {
  number: 8
}

```
现在有一个numberObj对象，内有一个默认参数number;

如果需要打印numberObj对象的默认number，无需为numberObj定义say函数，可以通过call、apply、bind直接复用NumberUtil对象的函数;

```js

num.say.call(numberObj);   //My default number is 8
num.say.apply(numberObj);  //My default number is 8
num.say.bind(numberObj)(); //My default number is 8
```

call、apply、bind的作用均为改变当前执行对象的this指针的指向;

call、apply、bind的第一个参数为指定当前执行对象其this指向的对象

<br/>
<br/>

### <font color=#4fc08d>\#</font>call、apply、bind区别

```js
num.sum.call(numberObj, 1, 2);     //Sum is 3
num.sum.apply(numberObj, [1, 2]);  //Sum is 3
var number_sum = num.sum.bind(numberObj);
number_sum(1, 2);  //Sum is 3
```

call、apply、bind的第二个参数为执行函数所需参数;

call与apply的用法基本相同，区别为call传参时需要分别传入所需参数,而apply传参则需要将所需参数组合为数组传入;

bind则时会返回一个新的函数，称为绑定函数，接受返回函数后再重新调用;

<br/>
<br/>

### <font color=#4fc08d>\#</font>call、apply的使用场景

数组之间追加

```js
var array1 = [12 , "foo" , {name:"Joe"} , -2458]; 
var array2 = ["Doe" , 555 , 100]; 
Array.prototype.push.apply(array1, array2); 
// array1 值为  [12 , "foo" , {name:"Joe"} , -2458 , "Doe" , 555 , 100] 
```

将数组二追加至数组一中

获取数组中的最大值和最小值

```js
var  numbers = [5, 458 , 120 , -215 ]; 
var maxInNumbers = Math.max.apply(Math, numbers),   //458
```

类（伪）数组使用数组方法

```js
var domNodes = Array.prototype.slice.call(document.getElementsByTagName("*"));
```

js中有许多类数组，他们有类似与数组的数据结构，却没有数组许多方法;

使用call和apply可以让类数组使用它们不包含的数组中的方法,如:dom选择器的返回值或arguments对象

<br/>
<br/>

### <font color=#4fc08d>\#</font>bind的使用场景

```js
var altwrite = document.write;
altwrite("hello");
```

结果：`Uncaught TypeError: Illegal invocation`

执行`document.write`时，当前函数this执行为document

赋值给`altwrite`并执行时，函数的this指向则变为了windows

windows对象中没有write函数所以会报非法调用异常，正确的方法为：

```js
altwrite.bind(document)("hello");
```
