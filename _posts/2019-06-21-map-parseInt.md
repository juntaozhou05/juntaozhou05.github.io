﻿---
layout: post
title: "['10','10','10','10','10'].map(parseInt) "
subtitle: ""
author: "ZJT"
header-style: text
tags:
  - js
---

### parseInt
parseInt() 函数解析一个字符串参数，并返回一个指定基数的整数 (数学系统的基础)。
```
const intValue = parseInt(string[, radix]);
```
string 要被解析的值。如果参数不是一个字符串，则将其转换为字符串(使用 ToString 抽象操作)。字符串开头的空白符将会被忽略。  

radix 一个介于2和36之间的整数(数学系统的基础)，表示上述字符串的基数。默认为10。
返回值 返回一个整数或NaN
```
parseInt(100); // 100
parseInt(100, 10); // 100
parseInt(100, 2); // 4 -> converts 100 in base 2 to base 10
```
**注意：**  
在radix为 undefined，或者radix为 0 或者没有指定的情况下，JavaScript 作如下处理：
- 如果字符串 string 以"0x"或者"0X"开头, 则基数是16 (16进制).
- 如果字符串 string 以"0"开头, 基数是8（八进制）或者10（十进制），那么具体是哪个基数由实现环境决定。ECMAScript 5 规定使用10，但是并不是所有的浏览器都遵循这个规定。因此，永远都要明确给出radix参数的值。
- 如果字符串 string 以其它任何值开头，则基数是10 (十进制)。
### map
map() 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。
```
var new_array = arr.map(function callback(currentValue[,index[, array]]) {
 // Return element for new_array
 }[, thisArg])
```
可以看到callback回调函数需要三个参数, 我们通常只使用第一个参数 (其他两个参数是可选的)。
```
const arr = [1, 2, 3];
arr.map((num) => num + 1); // [2, 3, 4]
```
回到我们真实的事例上
```
['1', '2', '3'].map(parseInt)
```
对于每个迭代map, parseInt()传递两个参数: 字符串和基数。
```
['1', '2', '3'].map((item, index) => {
	return parseInt(item, index)
})
```
即返回的值分别为：
```
parseInt('1', 0) // 1
parseInt('2', 1) // NaN
parseInt('3', 2) // NaN, 3 不是二进制
```
```
['10','10','10','10','10'].map(parseInt);
// [10, NaN, 2, 3, 4]
```
### 如何在现实世界中做到这一点
```
['10','10','10','10','10'].map(Number);
// [10, 10, 10, 10, 10]
```
