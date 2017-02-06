---
title: someting about function of javascript
date: 2017-02-06 17:26:29
tags:
- javascript
- 函数声明
- 函数表达式
- 声明提前
---

## 数声明与函数表达式

### 如何定义函数
*	函数声明
`function fName(arg1,arg2,...) {<!--function body-->}`

*	函数表达式
```
var fName = function(arg1,arg2,...) {<!--function body-->}
或者
var fname = function fName2(arg1,arg2,...) {<!--function body-->}
```

*	new Function 构造函数
`var fName = new Function();`

### 变量声明提前

用最直观的例子来呈现变量声明提前

```
var a = 'linyb';
(function() {
	console.log(a);
    var a = 'jjt';
    console.log(a);
})();
```

上述的代码运行结果是：
```
undefined
jjt
```

也就是说，`变量在声明它们的函数体以及这个函数体嵌套的任意函数体内都是有定义的。`在函数体内的局部变量覆盖了同名的全局变量，而且，程序只有在执行到var语句时，局部变量才真正被赋值。

以上代码等价于：
```
var a = 'linyb';
(function() {
	var a;
    console.log(a);
    var a = 'jjt';
    console.log(a);
})();
```

声明提前可以总结如下：
*	变量声明会提前到函数的顶部。
*	只是声明被提前，初始化不提前，初始化还在原来初始化的位置进行初始化。
*	在声明之前变量的值是undefined

### 函数声明提前

举个栗子

```
a();<!--函数声明-->
function a() { console.log("a") }

b();<!--函数表达式-->
var b = function() {console.log("b")}
```
上述代码执行结果：
```
a
Uncaught TypeError: b is not a function(…)
```
可以得出：使用函数声明的函数定义方法的时候，可以在任意位置调用函数。也就是说函数声明提前的时候，函数声明和函数体均提前了。

那么函数表达式为什么不能被提前？

同上面的变量声明提前一个道理，只是声明被提前，初始化不提前，初始化还在原来的位置进行初始化。
