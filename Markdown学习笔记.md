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
代码块的书写很方便。每行前面tab就可以。发现不能支持*中文*（现在看来是之前的markdown pro软件本身的问题，用Mou的话非常的ok)。

	#include<stdio.h>
	void main(){
		printf("Hello world.");
		return;
	}
	
###Fenced代码块
用包含三个反引号的line括起来表示. ~~实际上我觉得这就是行内代码的一种，只是书写时变化了点而已。~~  
修正：的确与行内代码是不同的。 应该是代码段的一种更加方便的书写方法。
	 
	
###水平线
用3个以上-、*就会得到水平线，如：

***

###Tables的书写

	First Header|Second Header|Third Header
	:-----------|:-----------:|:----------
	第一项		|第二项		  |第三项
	第四项|第五项|第六项

>上面的这段文字，在Mou中的解释与github或Markdown Pro中的不同。

First Header|Second Header|Third Header
:-----------|:-----------:|:----------
第一项		|第二项		  |第三项
第四项|第五项|第六项
	
>冒号表示对齐。可以写的好看点，但是为了大字方便，是没必要的。

##行级元素

###链接
分为:
* 行内链接 如:  [百度](http://www.baidu.com "我是title")。即，格式为: [链接文本](链接地址 "标题")
* 引用链接     

>还有种自动链接，直接用< >包含起来。如：<http://www.baidu.com> 。注意，必须写http。  
>书写Email的话也用这种自动连接的方式：<xxx@126.com>。

###强调
使用 *、_ 表示强调。如 _xx_。  
上面是斜体强调，还有种粗体强调用`**xx**, __xx__`的方法表示。
可以用\\符号来转义。

###删除线
使用2个～～符号包括起来表示。如：~~我是要被删除的。~~

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


##补充知识
MultiMarkdown针对Markdown的某些缺失的功能，所设计的超集。  
支持的语法有：

> * footnotes
* tables
* citations and bibliography (works best in LaTeX using BibTeX)
* math support
* automatic cross-referencing ability
* smart typography, with support for multiple languages
* image attributes
* table and image captions
* definition lists
* glossary entries (LaTeX only)
* document metadata (e.g. title, author, date, etc.)

另外，Markdown Extra也是类似的Markdown超集。
支持的语法有：

> * Inline HTML
* Markdown Inside HTML Blocks
* Header Id Attribute
* Fenced Code Blocks
* Tables
* Definition Lists
* Footnotes
* Abbreviations
* Emphasis
* Backslash Escapes

