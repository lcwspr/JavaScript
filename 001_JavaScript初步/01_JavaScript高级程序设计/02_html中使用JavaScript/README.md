# 在HTML中使用JavaScript

## 本章内容
* 使用\<script>元素
* 嵌入脚本与外部脚本
* 文档模式对于JavaScript的影响
* 考虑禁用JavaScript的场景

## 简介
* 只要一提到把JavaScript放到网页中，就不得不涉及web的核心语言--HTML。在当初开发JavaScript的时候，需要解决的一个重要问题就是如何做到让JavaScript既能够与HTML页面共存，又不会影响安歇页面在其他浏览器中的呈现效果。最终决定就是为Web增加统一的脚本支持。

### script 元素
* 向HTML页面插入JavaScript的主要方法就是使用script元素。html4.01为script定义了如下4个属性。
    * async 表示立即下载脚本，但不应妨碍页面中的其他操作。比如下载其他资源或等待加载其他脚本。只对外部脚本文件生效。
    * defer 表示脚本可以延迟到文档完全被解析和显示之后在执行。只对于外部脚本文件有效。
    * type 可选。可以看做是language的替代。基本使用text/javascript

### 两种引入方法
1. 直接在script标签中嵌入JavaScript代码，只需要指定type 属性，并放入代码。
    ```
        <script type='text/javascript'>
            function sayHi(){
                alert('Hi !');
            }
        </script>

    ```
    * 注意，在使用script嵌入JavaScript代码时，千万记住不要在代码的任何地方出现\</script>字符串。否则会产生错误。可以通过转义字符解决这个问题

2. 引入外部JavaScript文件。
    * src属性是必须的。指定外部JavaScript文件路径
        ```
            <script src='text.js' type="text/javascirpt"></script>
        ```
    * 另外通过script元素的src属性还可以包含来自外部域的JavaScript文件，千万注意

### 标签的位置
* 传统的做法将所有script元素放在页面的head元素中。可是在文档的head元素中包含所有的js文件，意味着必须全部的js代码被下载才开始显示内容。所以现今一般把全部的JavaScript放在body元素中页面内容的后面。

