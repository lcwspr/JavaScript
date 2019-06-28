# 基本概念

## 内容概述
* 语法
* 数据类型
* 流控制语句
* 函数

## 简述
* 任何语言的核心都必然会描述这门语言最基本的工作原理。而描述的内容通常都要涉及这门语言的语法、操作符、数据类型、内置功能等用于构建复杂解决方案的基本概念。ECMA-262通过叫做ECMAScript的‘伪语言’为我们描述了JavaScript的所有这些基本概念

## 语法
* ECMAScript的语法大量借鉴C及其他类C语言的语法。。

### 区分大小写
* 第一个概念就是ECMAScript中的一切变量(变量、函数名和操作符)都是区分大小写的.并且有的名称不能用于标识符，因为他们是关键字

### 标识符
* 所谓标识符，就是指变量、函数、属性的名字，或者函数的参数。标识符可以按照下列各式规则组合起来的一个或多个字符
    * 第一个字符必须是一个字母、下划线(_)、或一个美元符号($)
    * 其他字符可以是字母、下划线、美元符号或数字
    * 按照惯例，ECMAScript标识符采用驼峰大小写格式，就是第一个字母小写，剩下每个单词首字母大写

### 注释
* ECMAScript 使用C风格的注释，包括单行注释和块级注释。
    * // 单行注释
    * /* 块级注释 */

### 严格模式
* ECMAScript 5 引入严格模式的概念，为JavaScript定义了一种不同的解析与执行模型，ECMAScript 3 中的一些不确定行为将得到处理，某些不安全行为将会抛出错误。要在整个脚本中启用严格模式，可以在顶部添加如下代码 ： "use strict"
* 看起来像是字符串，但其实他是一个编译指示，用于告知JavaScript引擎切换到严格模式。
* 在函数的上方包含这条编译指示，可以指定函数在严格模式下执行。

### 语句
* ECMAScript中的语句以一个分号结尾；如果省略分号，则由解释器确定语句的结尾，虽然语句结尾的分号不是必须的，但是建议任何时候都不要省略他。这样可以删除多余的空格来压缩，另外加上分号有时候可以提升性能。
* 条件控制语句中，例如if,最好始终使用代码块。即便只有一条语句。

## 关键字和保留字
* 关键字
    * break, do, instanceof, typeof, case, else, new, var, catch, finally, return, void, continue, for, switch, while, debugger, function, this, with, default, if, throw, delete, in, try
* 保留字
    * abstract, enum, int, short, boolean, export, interface, static, byte, extends, long, super, char, final, native, synchronized, class, float, package, throws, const, goto, private, transient, debugger, implements, protected, volatile, double, import, public, let, yield

## 变量
* ECMAScript的变量是松散类型的，就是可以用来保存任何类型的数据。换句话说，每个变量仅仅是一个用于保存值的占位符而已。定义变量使用var关键字。
* `var message;` 这样就定义一个名为message的变量，可以用来保存任何值，未经过初始化的变量，会保存一个特殊值---undefined.
* 初始化语法 `var message = 'hi';`
* 初始化就是给变量赋一个值，因此以后修改变量值的同时能够修改值的类型
    ```
        var message = 'hi';
        message = 10;
    ```
    * 但不推荐，尽量不要修改变量的类型
* 使用var定义的变量将成为定义该变量作用域中的局部变量。(函数中定义的变量，出了函数作用域会被销毁)
* 如果直接使用一个没有声明过的变量那么会在当前作用域的最顶级定义一个全局变量，不要尝试这种做法

## 数据类型
* 简述
    * ECMAScript中有5种简单数据类型(也称为基本数据类型)：Undefined、Null、Boolean、Number、String 和 一种复杂数据类型 -- Object。
    * Object本质上是由一组无序的名值对组成的。ECMAScript不支持任何创建自定义类型的机制，所有的值最终都将是上述6中数据类型之一。由于、ECMAScript数据类型具有动态性，因此的确没有在定义其他数据类型的必要性了。

* typeof 操作符
    * 因为ECMAScript是松散类型的，所以需要有一种手段来检测给定变量的数据类型--typeof就是负责提供这方面信息的操作符，对一个值使用typeof操作符可能会返回下列某个字符串
        * "undefined" ---> 如果这个值未定义
        * "boolean" ---> 如果这个值时布尔值
        * "string" ---> 如果这个值时字符串
        * "number" ---> 如果这个值是数值
        * "object" ---> 如果这个值时数值
        * "function" ---> 如果这个值是函数
    * 有些时候，typeof操作符会返回一些令人迷惑但技术上却正确的值，从一些技术角度上讲，函数在ECMAScript中是对象，不是一种数据类型，然而，函数也确实有一些特殊的属性，因此通过typeof操作符来区分函数和其他对象是很有必要的。

* Undefined 类型
    * Undefined类型只有一个值，就是特殊的undefined.在使用var声明变量但未对其初始化时，这个变量的值就是undefined.
    * 比较未初始化变量与undefined 是相等的
    * 一般不存在显示的把一个变量设置为undefined值的情况。字面值的主要目的适用于比较，ECMA-262第三版之前没有规定这个值。引入他是为了区分空对象指针域未经初始化的变量.
    * 不过包含undefined值的变量与尚未定义的变量还是不一样的。 对于未经声明变量只能进行一项操作，就是使用typeof操作符检测其数据类型。(比较疑惑地是 对未经初始化的变量执行typeof操作符会返回undefined值，而对未声明的变量执行typeof操作符同样会返回undefined)，有逻辑上的合理性。因为两种变量从技术上看有本质区别，但无论对于那种变量也不能执行真正的操作
    * 即便未初始化的变量会自动被赋予undefined值，但显示的初始化变量依然是明智的选择，如果能够做到这一点，那么当typeof操作符返回"undefined"值时，我们就知道被检测的变量还没有被声明，而不是尚未初始化。

* Null 类型
    * Null类型是第二个只有一个值的数据类型，这个特殊的值是null.从逻辑角度，null值表时一个空对象指针，这正是使用typeof操作符检测null值时会返回'object'的原因。
    * 如果定义的变量准备在将来用于保存对象，那么最好将该变量初始化为null而不是其他值。这样一来，只要直接检查null值就可以知道相应的变量是否保存了一个对象的引用。
    * undefined值是派生自null值的，所以相等性测试要返回true。(null == undefined会返回true,因为这个操作符出于比较的目的会转换器操作数)
    * 注意，只要在保存对象的变量还没有真正的保存对象，那么就应该明确地让该变量保存null值。

* Boolean类型
    * Boolean类型是ECMAScript中使用最多的一种类型，该类型只有两个字面值，true和false. 虽然Boolean类型的字面值只有两个，但是ECMAScript中所有类型的值都有与这两个Boolean值等价的值。要将一个值转换为其对应的Boolean值，可以调用转型函数Boolean().
    * 其他数据类型对于boolean类型的转换。
        * String只要非空字符串都是真的。
        * Number除了0和NAN都是真的。
        * Object除了null都是真的。
        * undefined值都是假的

* Number类型