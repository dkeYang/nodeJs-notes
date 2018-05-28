# 标题设置
1. > 在文字下方添加=或者-，分别代表一级标题和二级标题。
2. > 在文字开头加上#，通过#的数量来标识几级标题（一共只有6级标题，1级标题的文字最大）
---
### eg 
 # hello word 
 ## hello world 

 hello wolrd
 -

# 块注释（blockquote）
* > 通过在文字开头添加>表示块注释。（当文字和> 之间添加五个blank时，块注释的文字会有变化）
  
  > this is a blockquote
# 斜体
* > 在内容的两端使用1个*或者_将需要设置为斜体的内容包裹起来。

   *italic*
# 粗体
* > 在内容的两端使用2个*或者_将需要设置为粗体的内容包裹起来。
  
  **bold**
# 无序列表
* > 在文字的开头使用*、+或者-实现无序列表，文字和符号之间需要添加空格。（建议在一个文档中只使用一种符号实现无序列表）

# 有序列表
* > 在文字的前面直接使用数字加.就可以实现有序列表

1. first
2. second

# 链接（Links）
### markdown中有两种方式实现链接，分别为内联方式和引用方式。
1. > `内联方式：This is an [example link](http://example.com) `

      [百度](http://www.baidu.com)

2. 

    引用方式：
    I get 10 times more traffic [Goole][1] than from[Yahoo][2] or [MSN][3]. 
     [1]:http://google.com 
     [2]:http://Yahoo.com 
     [3]:http://msn.com

this is [百度][1]and that is [google][2]
[1]:http://baidu.com[2]:http://google.com

# 图片
### 图片的处理方式和链接的处理方式非常相似
1. >`内联方式：![alt text](/path/img.jpg "title") title和路径之间需要一个空格`

     ![picture](./example.jpg 'example picture')

2. >`引用方式：![alt text][id]  [id]:/path/img.jpg "title"`

![picture][id] [id]:./example.jpg 'example picture'

# 代码（code）
1. > 简单文字出现一个代码框。使用`将代码两端包裹起来就好
2. > 大片文字需要实现代码框。在代码的每行使用tab或者四个空格

# 脚注（footnote）
    hello[^hello][^hello]:hi

# 下划线
* 在空白行下面添加三条---横线

# 更多请[查看](http://wowubuntu.com/markdown/#img)