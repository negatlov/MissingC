#Markdown学习笔记


>注意一点，不要在块级HTML元素内使用Markdown格式化命令，Markdown不会处理它们。比如你不要
在一个HTML块中使用 *emphasis* 这样的Markdown格式化命令。  
><br>
>Markdown中，以下字符支持使用反斜线转义：  
>>\   反斜线  
`   反引号  
\*   星号  
_   下划线  
{}  大括号  
[]  中括号  
()  小括号  
\#   井号    
\+   加号    
\-   减号（连字符）  
\.   句点  
\!   感叹号

##块级元素
>注意，该类元素前后得有空行隔开。

###段落与换行
段落间用一个～多个空行隔开。  
换行用>2个空格加换行符隔开。


###标题
有2种风格Setext与atx。

###引用块
用邮件列表种的>表示。

###列表
+ 无序用+、-、*加空格表示。
+ 有序用 数字 加 . 加 空格 表示。
	
注意，如果每条列表包含多段内容，则每段开始前必须加tab或4个空格

###代码块
代码块的书写很方便。每行前面tab就可以。发现不能支持*中文*。
	
	#include<stdio.h>
	void main(){
		printf("Hello world.");
		return;
	}
	
###水平线
用3个以上-、*就会得到水平线，如：

***

##行级元素

###链接
分为:
* 行内链接 如:  [百度](http://www.baidu.com "我是title")。即，格式为: [链接文本](链接地址 "标题")
* 引用链接     

>还有种自动链接，直接用< >包含起来。如：<http://www.baidu.com> 。注意，必须写http。

###强调
使用 *、_ 表示强调。
如 _xx_。
可以用\\符号来转义。

###行内代码
用反引号来包含起来。
>要在一个行内代码中使用反引号（\`）本身，用多个反引号作为定界符包住它：  
>\`\`There is a literal backtick (\`) here.\`\`

###图片
* 行内图片   
`![Alt text](/path/to/img.jpg)`  
`![Alt text](/path/to/img.jpg "Optional title")`
* 引用图片   
`![Alt text][id]`   
`[id]: url/to/image  "Optional title attribute"`




