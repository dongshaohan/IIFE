# IIFE
IIFE（immediately-invoked function expression），即立刻执行函数表达式。我们在写js过程中经常会遇到
`(function (){})()`和`(function (){}())`这样的写法，这两种都是IIFE的常见写法。
那它为什么要这么写呢？原理又是什么？我们先来了解一些函数的基本概念。

###函数声明
使用function关键字声明一个函数，再指定一个函数名，叫函数声明。
```javascript
function name () {
	// ...
}
```

###函数表达式
使用function关键字声明一个函数，但未给函数命名，最后将匿名函数赋予一个变量，叫函数表达式，这是最常见的函数表达式语法形式。
```javascript
var name = function () {
	// ...
}
```

###匿名函数
使用function关键字声明一个函数，但未给函数命名，所以叫匿名函数。匿名函数属于函数表达式，匿名函数有很多作用，赋予一个变量则创建函数，
赋予一个事件则成为事件处理程序或创建闭包等等。
```javascript
function () {
	// ...
}
```

###函数声明和函数表达式区别
* Javascript引擎在解析代码时，在当前作用域下会`函数声明提升`，也就是说无论函数声明的位置在哪，都能够优先调用。
而`函数表达式`必须等到Javascirtp引擎执行到它所在行时，才会从上而下一行一行地解析函数表达式。
* `函数表达式`后面可以加括号立即调用该函数，函数声明不可以，只能以xxx()形式调用。如下：

```javascript
name();  // 正常，因为函数声明提升
function name () {
	// ...
}

name();  // 报错，变量name还未保存对函数的引用，函数调用必须在函数表达式之后
var name = function () {
	// ...
}

var name = function () {
	console.log('Hello World');
}();
// 正确执行，当javascript引擎解析到此处时能立即调用函数

function name () {
	console.log('Hello World');
}();
// 语法错误

function () {
	console.log('Hello World');
}();
// 语法错误，虽然匿名函数属于函数表达式，但是未进行赋值操作
// javascript引擎将开头的function关键字当做函数声明，所以报错，要求需要一个函数名
```