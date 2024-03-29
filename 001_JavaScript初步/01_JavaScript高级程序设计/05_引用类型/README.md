# 第五章 引用类型

## 本章节内容
1. 使用对象
2. 创建并操作数组
3. 理解基本的JavaScript类型
4. 使用基本类型和基本包装类型

## 什么是引用类型
* 引用类型的值(对象)是引用类型的一个实例，在ECMAScript中，引用类型是一种数据结构用于将数据和功能组织在一起。他也常被称为类，但这种称呼并不妥当。尽管ECMAScript从技术上面讲是一门面向对象的语言，但是它不具备传统的面向对象语言所支持的类和接口等基本结构。引用类型有时候也被称为对象定义，因为他们描述的是一类对象所具有的属性和方法。
* 对象是某个特定引用类型的 ***实例*** 。新对象是使用new操作符后跟一个 ***构造函数*** 来创建的。构造函数本身就是一个函数，不过该函数是出于创建新对象的目的而定义的。
    ```
        var person = new Object();
    ```
    * 这行代码创建了Objcet引用类型的一个新的实例，然后把该实例保存在了变量person中，使用的构造函数是Object，他只为新对象定义了默认的属性和方法。ECMAScript提供了很多原生引用类型，以便开发人员是以实现常见的计算任务。

## Object类型
* 目前，我们看到的大多数引用类型值都是Object类型的实例，而且Object也是ECMAScript中使用最多的一个类型，虽然Object的实例不具备多少功能，但对于在英勇程序中存储和传输数据而言，他们是非常理想的选择。

### 创建Object类型的两种方式
1. 使用new操作符后跟Object() 构造函数
    ```
        var person = new Object();
        person.name = 'lcwspr';
        person.age = 29;
    ```
2. 使用 ***对象字面量*** 表示法.
    * 是对象定义的一种简写形式。目的在于简化创建包含大量属性的对象的过程。
        ```
            var person = {              // 表示对象字面量的开始
                name : 'lcwspr',        // 使用逗号分隔不同属性
                age : 28
            }
        ```
    * 使用对象字面量语法时，属性名也可以使用字符串
        ```
            var person = {
                "name": 'Nicholas',
                "age": 29,
                5: true         // 注意这里包含的数值属性会自动转换为字符串
            }
        ```
    * 使用对象字面量语法时，如果留空其花括号，可以定义只包含默认属性和方法的对象
        ```
            var person = {};   // 与 new Object() 相同
            person.name = 'lcwspr';
            person.age = 39;
        ```
        * 注意，在通过对象字面量定义对象时，实际上不会调用Object构造函数，早期浏览器版本会，但之后的就不会了。
    * 虽然可以使用前面介绍的任何一种方法来定义对象，但是开发人员更加青睐对象字面量语法，因为这种语法要求的代码量少，而且能够给人封装数据的感觉。实际上，对象字面量也是向函数传递大量可选参数的首选方式，如下：
        ```
            fucntion displayInfo(args){
                var output = '';
                
                if (typeof args.name == 'string'){
                    output += 'Name: ' + args.name + '\n';
                }
                
                if(typeof args.age == 'number'){
                    output += 'Age: ' + args.age + '\n'; 
                }

                alert(output);
            }

            displayInfo({
                name: 'lcwspr',
                age: 29
            });

            displayInfo({
                name: 'luck'
            })
        ```
        * 函数displayInfo()接收一个名为args的参数，这个参数可能带有一个名为name或者age的属性，可能这两个属性都有或者都没有，在这个函数内部，我们通过typeof操作符来检测每个属性是否存在，然后进行相关操作。然后调用函数时，每次都使用了一个对象字面量来指定不同的数据，这两次调用传递的参数虽然不同，但函数都能正常运行。
        * 这种参数传递模式最适合需要向函数传入大量可选参数的情形，一般来说。命名参数虽然容易处理，但是再有多个可选参数的情况下就会显得不够灵活，一般最好的做法是对于那些必须的值使用命名参数，而使用对象字面量来封装多个可选参数。

### 访问对象属性的两种方法
* 一般来说，访问对象的属性时使用的都是点语法表示法，这也是很多面向对象语言中通用的语法。
    * 不过在js中也可以使用方括号表示法来访问对象的属性，在使用方括号语法时，应该将要访问的属性以字符串的形式放在方括号中。
    ```
        alert(person['name']);          // 优点是能够通过变量访问属性
        alert(person.name);
    ```
    * 能够使用变量来访问
        ```
            var propertyName = 'name';
            alert(person[propertyName]);        // 'lcwspr'
        ```
    * 如果属性名中包含会导致语法错误的字符，或者属性名使用的是关键字或者保留字，也可以使用方括号表示法。
        ```
            person['first name'] = 'lcwspr';
        ```
        * 一般除非必须使用变量来访问属性，否则应该使用点表示法。

## Array 类型
* 除了Object类型之外，Array类型恐怕是ECMAScript中最常用的数据类型了，而且，ECMAScript中的数组与其他多数语言中的数组有着很大的区别。虽然ECMAScript数组与其他语言中的数组都是数据的有序列表，但是ECMAScript中的数组每一项都可以保存任何数据类型。并且ECMAscript中数组的大小是可以动态调整的。可以随着数据的增长自动添加内容以容纳新数据。
* 区别总结
    * 数组的每一项可以是任意类型
    * 数组的大小是可以动态改变的

### 数组的创建方式
1. 使用Array()构造函数
    * 语法
        `var colors = new Array();`
    * 注意
        * 如果知道数组要保存的项目数量，可以给构造函数传递该数量。该数量自动变成length属性的值。
            `var colors = new Array(20); `
        * 也可以向Array构造函数传递数组中应该包含的项。
            `var colors = new Array('red', 'blue', 'green')`
        * 也可以只传递一个值创建数组，如果传递的是数值，那么就会按照该数值创建包含给定项数的数组，如果传递的是其他类型的值，那么会包含该值的数组
            ```
                var colors = new Array(2)   // 创建一个包含2个元素的数组
                var names = new Array('Greg'); // 创建一个包含一个'Greg'的数组
            ```
        * 其实在使用Array构造函数是也可能省略new.
2. 使用数组字面量表示法 (由一对包含数组项的方括号表示)
    ```
        var colors = ['red', 'blue', 'green']; // 创建一个包含3个字符串的数组
        var names = [];  // 创建空数组
        var values = [1,2,]  // 不要这样，可能会创建一个2/3元素的数组
        var values = [,,,,,]  // 不要这样，可能会创建一个5/6元素的数组
    ```
    * 除了早期版本，现在数组字面量也不再调用Array()构造函数

### 数组设置和读取值
* 设置和读取值的时候要使用方括号并且提供相应值的基于0的数字索引， ***如果设置某个值的索引超过了先有数组的项目数，那么数组会自动增加到该索引值加1的长度。***
    ```
        var colors = ['red', 'blue', 'green'];
        alert(color[0]);
        color[3] = 'black';
    ```
    * 数组的项目数保存在其length属性中，这个属性始终会返回0或更大的数值。
    * 数组的length属性很有特点，不是只读的，可以通过设置这个属性向数组总添加或者移除属性。
    * 使用length可以非常方便的在数组末尾添加新的项目。
        ```
            var colors = ['red', 'blue', 'green'];
            colors[colors.length] = 'black';
            colors[colors.length] = 'brown';

            // length永远是下一项应该填入的位置
        ```
### 检测数组
* 如何确定一个对象是不是数组的经典问题，对于一个网页或者一个全局作用域，使用instanceof 操作符就能够得到满意的答案
    ```
        if(value instanceof Array){
            // 对于数组执行某些操作
        }
    ```
    * 但是instanceof假定只有一个全局环境，如果网页中包含多个框架，那么就存在两个以上不同的全局执行环境，就有两个以上版本的Array构造函数。如果从一个框架传入一个数组到另一个框架，那么两个版本的Array分别具有各自不同的构造函数。
        * 于是ECMAScript5新增了 Array.isArray()方法，用于确定某个值是不是数组。不管在哪创建

### 转换方法
* 如前所述，所有的对象都具有toLocaleString()、toString()和valueOf()方法。
    * 调用toString()方法会返回由数组中每个值的字符串形式拼接而成的一个以逗号分割的字符串。会调用每一项的toString()方法
    * valueOf()
    * toLocaleString() 方法，会调用每一个元素的toLocaleString方法。