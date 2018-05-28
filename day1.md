## What is node.js?
>js是脚本语言，脚本语言需要一个解析器才能运行。对于写在html中的js，浏览器充当了解析器的角色。而对于需要独立运行的js，NodeJs就是一个解析器。

> 每一种解析器都是一个运行环境，不但允许js定义各种数据结构，进行各种计算，还允许js使用运行环境提供的内置对象和方法去做一些事情。例如运行在浏览器中的js的用途是操作DOM，浏览器就内置了document之类的类似对象。而运行在NodeJs中的Js的用途是操作磁盘文件或搭建http服务器，NodeJs就相应的提供了fs、http等内置对象。

## 用处
> NodeJs的作者说，他创造NodeJs的目的是为了实现高性能web服务器，他首先看中的是事件机制和异步IO模型的优越性，而不是Js。但是他需要选择一种编程语言实现他的想法，这种语言不能自带IO功能，并且，需要良好的支持事件机制。Js没有自带IO功能，天生就用于处理浏览器中的DOM事件。

>如他所愿，NodeJs