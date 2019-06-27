# JavaScript 简介

## 本章内容
1. JavaScript 历史回顾
2. JavaScript 是什么
3. JavaScript 与 ECMAScript 的关系
4. JavaScript 的不同版本

## 简述
* JavaScript 诞生于1995年，当时的主要目的是处理以前由服务器端语言(Perl)负责的一些输入验证操作。在JavaScript诞生之前，必须把表单数据发送到服务器端才能够确定用户的输入是否合法.Netscape Navigator希望通过JavaScript来解决这个问题。当时的年代网速很慢，能够在客户端完成一些基本的验证任务绝对是令人兴奋地。
* 从此以后，JavaScript 逐渐成为了市面上常见浏览器的一项特色功能，如今，JavaScript的用途早已不在局限在简单的数据验证，而是具备了与浏览器窗口及其内容等几乎所有方面交互的能力。如今的JavaScript已经成为了一门功能全面的编程语言。作为web重要的组成部分，javascript的重要性已经不言而喻。
* JavaScript从一个简单的输入输出验证器发展成为一门非常强大的编程语言，完全是出乎人们的意料的，JavaScript是一门非常简单的语言，又是一门非常复杂的语言，因为学会使用它只需要片刻功夫，而真正掌握它则需要数年时间。想要全面理解和掌握JavaScript的关键在于弄清楚他的本质、历史、局限性

## JavaScript 简史
* 在Web日益流行的同时，人们对于客户端脚本语言的需求也越来越强烈。那个时候，绝大多数用户都在使用速度仅仅为28.8kbit/s的"猫"上网，但是网页的大小和复杂性却不断增加，为了完成简单的表单验证而频繁与服务器交换数据只会加重用户的负担。当时走在技术革新最前沿的 Netscape 公司，决定着手开发一种客户端语言，用来出来这种简单的验证
* 当时就职于 Netscape 公司的布兰登.艾奇(Brendan Eich),开始着手为计划于1995年二月发布的 Netscape Navigator 2 开发一种名为LiveScript的脚本语言---该语言将同时在浏览器和服务器中使用(服务器端名为 LiveWire ). 为了赶在发布日期前完成 LiveScript 的开发，Netscape与Sun公司建立了一个联盟。在 Netscape Navigator 2 正式发布前夕，Netscape 为了搭上媒体热吵的Java顺风车，临时把LiveScript改名为JavaScript.
* 由于 JavaScript 1.0 获得了巨大的成功，Netscape随即在 Netscape Navigator 3 中又发布了 JavaScript 1.1. 于此同时，微软决定向Navigator竞争的自家产品 Internet Explorer 浏览器投入更多的资源。在 Netscape Navigator 3发布不久后，微软就在其 Internet Explorer 3中加入了名为JScript的JavaScript实现
* 微软推出其JavaScript实现意味着有两个不同版本的JavaScript版本：Netscape Navigator中的JavaScript、Internet Explorer中的JScript。但是此时业界却没有一个标准规定JavaScript的语法和特性，两个不同版本并存的局面已经完全暴露了这个问题，JavaScript的标准化问题被提上了日程。
* 1997年，以JavaScript 1.1 为蓝本的建议被提交给了欧洲计算机制造协会(ECMA).该协会制定39号技术委员会负责标准化一种"通用、跨平台、供应商中立的脚本语言的语法和语义"，经过数月努力他们完成了ECMA-262---定义了一种名为ECMAScript的新脚本语言的标准
* 第二年ISO/IEC 也采用了ECMAScript作为标准。以后浏览器厂商就开始致力于将Ecmascript作为各自JavaScript实现的基础。。。

## JavaScript 实现
* 虽然JavaScript和Ecmascript通常被人们用来表达相同的含义，但是JavaScript的含义却比ECMA-262中规定的要多得多，一个JavaScript实现又该有下列三个不同的部分组成
    1. 核心 (ECMAScript)
    2. 文档对象模型 (DOM)
    3. 浏览器对象模型 (BOM)

### ECMAScript
* 由ECMA-262定义的ECMAScript与WEB浏览器没有任何依赖关系，实际上这门语言本身并不包括输入和输出定义。ECMA-262定义的只是这门语言的基础，在这个基础之上可以构建更加完善的脚本语言。WEB浏览器只是ECMAScript实现的宿主环境之一。宿主环境不仅提供基本的ECMAScript实现，同时也会提供该语言的拓展。使得该语言与环境之间对接交互。而这些操作(如DOM)，则利用ECMAScript的核心类型和语法提供更多更加具体的功能，以便实现针对环境的操作。其他宿主环境包括Node(一种服务端的JavaScript平台)和Adobe Flash.

* ECMAScript中具体规定的内容
    1. 语法
    2. 类型
    3. 语句
    4. 关键字
    5. 保留字
    6. 操作符
    7. 对象
* ECMAscript就是对实现该标准规定各个方面内容的语言的描述，JavaScript实现了ECMAScript，Adobe ActionScript同样也实现了ECMAScript。
* ECMAScript版本
    * ECMAScript的不同版本又称为版次，ECMA-262的第一版本质上与Netscape的JavaScript 1.1 相同。不过删除了针对于浏览器的代码并做了较小的改动。ECMA-262要求支持Unicode标准，而且对象也变为了与平台无关的
    * ECMA-262第二版主要是编辑加工的结果，为了与ISO/IEC-16262保持一致，没有新增特性
    * ECMA-262第三版才是对于该标准的第一次真正的修改，修改内容涉及字符串处理、错误定义和数值输出。这一版还新增了对于正则表达式、新控制语句、try-catch异常处理的支持，并围绕标准的国际化做出了一点小修改
    * ECMA-262第四版对于这门语言进行了全面的修订，由于JavaScript在web上的流行，开发人员纷纷建议修订ECMAScript。作为回应ECMA T39重新谋划这门语言，结果出台后的标准几乎定义了一门全新的语言，第四版包含强类型变量、新语句和新的数据结构、真正的类和经典继承，但与此同时，也有一个下属小组提出了一个名为ECMAScript3.1的替代性建议，只对于该语言进行少量的修改，这个小组任务4版对于这门语言改动过大，最终ECMAScript3.1的支持超过了第四版。
    * Ecmascript 3.1 成为ECMA-262 第五版，与2009年12月3日发布，力求澄清3版中已知的各种歧义并添加新功能，包括原生JSON对象、集成的方法和高级属性定义另外包含一种严格模式
* ECMAScript兼容
    * 支持ECMA-262描述的所有 类型、值、对象、属性、函数以及程序句法和语义
    * 支持Unicode标准
    * 此外兼容的实现还可以进行下列拓展
        * 添加ECMA-262没有描述的 “更多类型、值、对象、属性、和函数”
        * 支持ECMA-262没有定义的“程序和正则表达式语法”（就是说可以修改和拓展内置的正则表达式语法）

### 文档对象模型(DOM)
* 文档对象模型(DOM) 是针对XML但经过拓展用于HTML的应用程序编程接口(API).DOM把整个页面映射为一个多层节点结构。HTML或者XML页面中的每个组成部分都是某种类型的节点，这些节点又包含者不同类型的数据。
* 通过DOM创建一个表示文档的树形图，开发人员获得了控制页面内容和结构的主动权。借助DOM提供的API，开发人员可以轻松自如的删除、添加、替换或者修改任何节点。
* 为什么要使用DOM
    * 在 Internet Explorer 4和Netscape Navigator 4分别支持的不同形式的DHTML(Dynamic HTML)基础上，开发人员首次无序重写加载网页，就可以修改其外观和内容。然而，DHTML在给Web技术发展带来巨大进步的同时，也带来了巨大的问题，由于微软和Netscape在开发DHTML方面各持己见，过去只编写一次HTML页面就能在任何浏览器运行的时代结束了
    * 对于开发人员，如果想保持Web跨平台的天性，就必须额外多做一些工作。而人们真正担心的是，如果不过微软和Netscape加以控制，web开发会出现技术上的两强割据，浏览器互不兼容的局面，此时，负责制定Web通信标准的W3C(World Wide Web Consortium,万维网联盟)开始着手规划DOM。
* DOM级别
    * DOM1级与1998年10月成为W3C推荐标准，由两个模块组成DOM核心(DOM Core)和DOM HTML。
        * DOM Core
            * 规定的是如何映射基于XML的文档结构，以便简化对文档中任意部分的访问和操作
        * DOM HTML
            * 在DOM核心的基础上加以拓展，添加了针对于HTML的对象和方法
    * 注意：DOM并不是只是针对于JavaScript的，很多其他语言都实现了DOM。不过在Web中，基于ECMAScript实现的DOM地区成为了JavaScript这门语言的重要组成部分。
    * DOM2级比DOM1级要宽泛很多，DOM2级在原来的基础上有扩充了鼠标和用户界面事件、范围、遍历等细分模块，并且通过对象接口增加了对于CSS（Cascading style Sheets）的支持。DOM1级中的DOM核心模块也经过拓展开始支持XML命名空间。 DOM2级引入了如下模块
        * DOM视图
            * 定义跟踪不同文档视图的接口
        * DOM事件
            * 定义了事件和事件的处理接口
        * DOM样式
            * 定义了基于CSS为元素应用样式的接口
        * DOM遍历和范围
            * 定义了遍历和操作文档树的接口
    * DOM3级 则进一步扩充DOM
        * 引入统一方式加载和保存文档的方法
        * 新增验证文档的方法        

### 浏览器对象模型 (BOM)
* 浏览器支持可以访问和操作浏览器窗口的浏览器对象模型(BOM).开发人员使用BOM可以控制浏览器显示的页面以外的部分。而BOM真正与众不同的地方还是他作为JavaScript实现的一部分但却没有相关的标准，这个问题在HTML5中得到了解决，HTML5致力于把很多BOM功能写入正式规范
* 根本上BOM只处理浏览器窗口和矿建，但人们习惯把所有针对浏览器的JavaScript拓展算作浏览器的一部分
    1. 弹出新浏览器窗口的功能
    2. 移动、缩放、关闭浏览器窗口的功能
    3. 提供浏览器详细信息的navigator对象
    4. 提供浏览器所加载页面详细信息的location对象
    5. 提供用户显示器分辨率详细信息的screen对象
    6. 对于cookies的支持
    7. 向XMLHttpRequest和IE的ActiveXObject这样的自定义对象
* BOM由于没有标准可以遵循，所以每个浏览器都会有自己的实现，虽然有一些事实上的标准，例如要有window对象和navigator对象，但每个浏览器都会为这两个对象定义自己的属性方法。

## 小结
* JavaScript是一种专门与网页交互而设计的脚本语言，由三个不同的部分组成
    * ECMAScript，由ECMA-262定义，提供核心语言功能
    * 文档对象模型，提供访问和操作网页内容的方法和接口
    * 浏览器对象模型，提供与浏览器交互的方法
    