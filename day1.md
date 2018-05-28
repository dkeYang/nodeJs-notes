## 是什么?
>js是脚本语言，脚本语言需要一个解析器才能运行。对于写在html中的js，浏览器充当了解析器的角色。而对于需要独立运行的js，NodeJs就是一个解析器。

> 每一种解析器都是一个运行环境，不但允许js定义各种数据结构，进行各种计算，还允许js使用运行环境提供的内置对象和方法去做一些事情。例如运行在浏览器中的js的用途是操作DOM，浏览器就内置了document之类的类似对象。而运行在NodeJs中的Js的用途是操作磁盘文件或搭建http服务器，NodeJs就相应的提供了fs、http等内置对象。

## 有什么用？
> NodeJs的作者说，他创造NodeJs的目的是为了实现高性能web服务器，他首先看中的是事件机制和异步IO模型的优越性，而不是Js。但是他需要选择一种编程语言实现他的想法，这种语言不能自带IO功能，并且，需要良好的支持事件机制。Js没有自带IO功能，天生就用于处理浏览器中的DOM事件。

>如他所愿，NodeJs在服务端活跃起来，出现了大批基于NodeJs的web服务。而另一方面，NodeJs让 *前端er*如获神器，终于可以让自己的能力覆盖范围跳出浏览器窗口，更大批前端工具如雨后春笋。

>因此，对于前端而言，虽然不是人人都要拿NodeJs写一个服务器程序，但简单可至使用命令交互模式调试js代码片段，复杂可至编写工具提升工作效率。


## 如何安装？
### 1. 安装程序
>NodeJs提供了一些安装程序，都可以在[nodejs.org](https://nodejs.org/download/)这里下载并安装。<br/>
Windows系统下,选择和系统版本匹配的.msi后缀的安装文件。Mac OS X系统下，选择.pkg后缀的安装文件。

### 2. 编译安装
>Linux系统下没有现成的安装程序可用，虽然一些发行版可以使用apt-get之类的方式安装，淡不一定能安装到最新版。因此LInux系统下一般使用以下编译方式安装NodeJs。<br>
&nbsp;&nbsp;1.确保系统下g++版本在4.6以上，python版本在2.6以上;<br>
&nbsp;&nbsp;2.从[nodejs.org](https://nodejs.org/download/)下载tar.gz后缀的NodeJs最新版源代码包并解压到某个位置;<br>
&nbsp;&nbsp;3.进入解压到的目录，使用以下命令编译和安装：

    $ ./configure
    $ make
    $ sudo make install

## 如何运行？
#### 打开终端，输入node进入命令交互模式，可以输入一条代码语句后立即执行并显示结果，例如：

    $ node
    > console.log('hello world');
    hello world

#### 如果需要运行一大段代码的话，可以先写一个JS文件再运行。如有以下hello.js

    (function(){
        console.log('hello world');
    })();

#### 写好后在终端输入node hello.js运行，结果如下：
    $ node hello.js
    hello world


## 权限问题
#### 在Linux系统下，使用NodeJs监听80或443端口提供HTTP(S)服务时需要root权限，有两种方式可以做到。
1. >使用sudo命令运行NodeJs.
    
        $ sudo node hello.js`

2. >使用*chmod +s*命令让NodeJs总是以root权限运行，具体做法如下

        $ sudo chown root /usr/local/bin/node
        $ sudo chmod +s /usr/local/bin/node
    >因为这种方式让任何js脚本都有了root权限，不太安全。因此在需要很考虑安全的系统下不推荐使用。

## 模块
#### 编写稍大一点的程序时一般都会将代码模块化。在NodeJs，一般将代码合理拆分到不同的Js文件中，每一个文件就是一个模块，而文件路径就是模块名。在编写每个模块时，都有require、exports、module三个预先定义好的变量可供使用。
- ***require*** 
  >**reqiure**函数用于在当前模块中加载和使用别的模块，传入一个模块名，返回一个模块导出对象。模块名可以使用相对路径或绝对路径。另外，模块名中的.js扩展名可省略。

        var foo1 = require('./foo');
        var foo2 = require('./foo.js);
        var foo3 = require('/home/user/foo');

  > 另外，可以使用以下方式加载和使用一个JSON文件

        var data = require('./data.json');

- ***exports***
  >**exports**对象就是当前模块的导出对象，用于导出模块公用方法和属性。别的模块通过*require*函数使用当前模块时得到的就是当前模块的**exports**对象。

        exports.hello = function(){
            console.log('hello world');
        }

- ***module***
  >通过**module**对象可以访问到当前模块的一些相关信息，但最多的通途还是替换当前模块的导出对象。例如模块导出对象，默认是一个普通对象，如果想改成一个函数的话，可以使用以下方式

        module.exports = function(){
            console.log('hello world');
        }

  >以上代码中，模块默认导出对象被置换为一个函数。

- ***模块初始化***
  >一个模块中的JS代码仅在模块第一次被使用时执行一次，并在执行过程中初始化模块的导出对象。之后，缓存起来的导出对象被重复利用。

- ***主模块***
  >通过命令行参数传递给NodeJs以启动程序的模块被称为主模块。主模块负责调度组成整个程序的其他模块完成工作。例如通过以下命令启动程序时，main.js就是主模块：

        $ node main.js

    > 例如有以下目录:

        - /home/user/hello/
          - util/
             counter.js
          main.js

    >其中counter.js内容如下：

        var i = 0;
        function count(){
            return ++i;
        };
        export.count = count;

    >该模块内部定义了一个私有变量i，并在exports对象导出了一个公有方法count。

    >主模块main.js内容如下：

        var counter1 = require('./util/counter');
        var counter2 = require('./util/counter');

        console.log(counter1.count());
        console.log(counter2.count());
        console.log(counter2.count());

    >运行该程序的结果如下：

        $ node main.js
        1
        2
        3
    >可以看到，counter.js并没有因为被require了两次而初始化两次。

## 二进制模块
#### 虽然一般我们使用js编写模块，但NodeJs也支持使用C/C++编写二进制模块。编译好的二进制模块除了文件扩展名是 *\.node*外，和Js模块的使用方式相同。虽然二进制模块能使用操作系统提供的所有功能，拥有无限的潜能，但难以跨平台使用。

## 小结
1. >NodeJs是一个Js脚本解析器，任何操作系统下安装NodeJs本质上做的事情都是把NodeJs执行程序复制到一个目录，然后保证这个目录在系统PATH环境变量下，以便终端下可以使用 *node*命令；
2. >终端下直接输入 *node*命令可进入命令交互模式（生成repl执行环境），很适合用来测试一些JS代码片段，比如正则表达式；
3. >NodeJs使用CMD规范，主模块作为程序入口点，所有模块在执行过程中只初始化一次；
4. >除非JS模块不能满足需求，否则不要轻易使用二进制模块。