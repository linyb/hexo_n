---
title: About box-shadow
date: 2017-1-7 17:22:22
tags:
- Javascript
- OOP
- this
---

## this 来聊三块钱的呗~

### 涵义

`this`，至关重要的存在。
总是返回一个对象，简言之，就是返回属性或方法“当前”所在的对象。
```
this.property
```
上面代码中，`this`表示`property`属性当前所在的对象
```
var person = {
	name: 'linyb',
    getName: function() {
    	return 'name:' + this.name;
    }
};
person.getName();//"name:linyb"
```
上面代码中，`this.name`表示`getName`方法所在的当前对象的`name`属性。调用`person.getName`时，`getName`方法所在的当前对象是`person`,所以返回的是`person.name`。

由于对象的属性可以赋给另一个对象，所以属性所在的当前对象是可变的。即`this`的指向是可变的。

```
var A = {
	name: 'A',
    getName: function() {
    	return 'name=' + this.name;
    }
}

var B = {
	name : 'B'
}

B.getName = A.getName;
B.getName(); //"name=B"
```
上面代码中，`A.getName`属性被赋给`B`，于是`B.getName`中`this`的当前所在对象是`B`,所以返回的是`B.name`。

等价于

```
function f() {
	return 'name=' + this.name;
}

var A = {
	name: 'linyb',
    getName: f
}

var B = {
	name: 'jjt',
    getName: f
}

A.getName() //"name=linyb"
B.getName() //"name=jjt"

```

上面的内码中，函数`f`的内部使用了`this`关键字，伴随这`f`所在的对象的不同，`this`的指向也不同。

```
var C = {
	name: 'zmj',
    getName: function() {
    	return 'name=' + this.name;
    }
}

var name = 'coco'
var d = c.getName;
d();//"name=coco"
```

上面代码中，`C.getName`被赋值给对象`d`,而`d`所在的对象是顶层对象`window`。

综上所述，`this`可以说是所有函数运行时的一个隐藏参数，指向函数的运行环境。

### 使用场合

##### 全局环境

在全局环境中使用`this`,它指的就是顶层对象`window`.

```
this === window // true

function f() {
	console.log(this === window); //true
}
```

上面的代码说明，不管在函数内部还是外部，只要是在全局环境下进行，`this` 就是指向顶层对象 `window`


##### 构造函数

构造函数中的`this`，指的是实例对象。

```
var Obj = function(name) {
	this.name = name;
}

Obj.prototype.getName = function() {
	return this.name;
}

var o = new Obj('linyb');
o.getName(); //"linyb"
o.name; //"linyb"
```

上面的代码中定义了个构造函数`Obj`,由于`this`指向实例对象，所以`this.name`表示实例对象有一个`name`属性，`getName`方法可以返回该属性。

##### 对象的方法

```
var _obj = {
	foo: function() {
        console.log(this);
    }
}
_obj.foo(); //Object{}

```

上面代码中，`_obj.foo` 方法执行时，它的内部`this`指向`_obj`。只有在`_obj`对象上调用`foo`，`this`才指向`_obj`,其他用法，`this`都指向代码块当前所在对象。


