#The C Programming Language

##Chapter 1: A Tutorial Introduction
>这章概要介绍了C的基础语法。  

###Pg 7.
  
1.  Argument和Parameters之间到底有什么区别？   
Argument是实参（函数调用时）、Parameters是形参（函数声明时）。

###Pg 14.
2. 深入理解Constant。   
Constant很容易和Literal与Macro混淆。
	Literal is a notation for representing a fixed value in source code.  Literals are often used to initialize variables。For example: `int i = 1;`。  
	
	A constant is an identifier whose associated value cannot typically be altered by the program during its execution。

	_There are several main ways to express a data value that doesn't change during program execution that are consistent across a wide variety of programming languages._
	* Literal
	* Symbolic macro 在这本书中，被叫作Symbolic Constants
	* Constant variable    

>注意，macro代码后面都没有分号。所以#include #define语句中都无分号结尾。
>
>Compilers generally put static constants in the text section of an object file along with the code itself, as opposed to the data section where non-const initialized data is kept, though some have an option to produce a section specifically dedicated to constants, if so desired. Memory protection can be applied to this area to prevent overwriting of constant variables by errant pointers.

###Pg 30.
3. Char与string的关系。   
当一个字符串出现在代码中时，实际上是被保存为以\0结尾的char数组。

###Pg 31.
4. Automatic Variable、 Local Variable与 lexical/my/private variable的关系。   
它们实际上是指同一种variable.只是叫法的区别。C/C++中叫 Automatic Variable。Java中叫Local Variable。而Perl中就用的第三中叫法。(参考自 wikipedia)。

5. External Variable学习。  
实际上，函数内的extern关键词就是为了让函数知道在外面有这个变量存在，然后才能拿过来用。   
不过，在源码中，当函数外面的变量是在该函数的前面书写时，函数默认是知道有该外部变量的，所以extern关键词是可以省略滴。。

##Chapter 2: Types, Operates, and Expressions

>从这章，我应该知道c语言的数据类型有哪些，操作符的分类以及优先级的判定。

###Pg 35.
1. 关于变量名的选择。  
	* 变量名不要用\_开头。库程序采用了。
	* 区分大小写。
	* 小写表示一般变量，大写表示Symbolic Macro。
	* 一般推荐短名表示局部变量，长名表示外部变量。
	
###Pg 36.
2. 数据类型探究。  
4个basic data type: char int float double。  
short/long qualifier(限定词) 用于限定int类型时可以省略int。  
signed/unsigned qualifier 用于限定char、int。  
long qualifier可以限定double。

###Pg 41.
3. 操作符分类。
	* Arithmetic Operators  <pre>%是取余操作符</pre>
	* Relational Operators
	* Logical Operators
	* Increment and Decrement Operators
	* Bit Operators 
		* bitwise
		* shift
	* Assignment Operators
	* Conditional Operators
	

##Chapter 4: Functions And Program Structure
>弄懂三类变量

###Pg 80. 
>该页关于external variable及其scope的讲解很透彻。

1. External Variable彻底学习。
	* 一个外部变量的scope是：from the point at which it is declared to the end of the file being compiled. 要注意其中的declared这个词。想明白为什么不是defined。
	* external variable的definition and declaration是不同的。
		* A declaration announces the properties of a variable。（主要是类型）。
		* A definition除了有声明的意义，还causes storage to be set aside.
	* 如果一个外部变量在被定义前就被引用，或者它的定义是在别的file中，则，声明该外部变量就是必须的。
	* 初始化外部变量只能在定义中进行。
	
###Pg 83.
2. Static Variables的理解。  
Static限制符的用处是使得external variable or function 的scope 被限制在它们所在的file中。别的文件中代码不能在引用到它们。  
另外，static还可以用在internal variable(automatic variable/local variable)中， 它的作用是使得该变量在函数被调用结束后依然存在。 不知道啥用。。。 
才google了下，发现了好东西，更好的总结了static的用处，并说明了internal static variable的用处：

>This confusion(The Q: Internal static variables in C, would you use them?) usually comes about because the static keyword serves two purposes.

>When used at file level, it controls the visibility of its object outside the compilation unit, not the duration of the object (visibility and duration are layman's terms I use during educational sessions, the ISO standard uses different terms which you may want to learn eventually, but I've found they confuse most beginning students).

>Objects created at file level already have their duration decided by virtue of the fact that they're at file level. The static keyword then just makes them invisible to the linker.

>When used inside functions, it controls duration, not visibility. Visibility is already decided since it's inside the function - it can't be seen outside the function. The static keyword in this case, causes the object to be created at the same time as file level objects.

>Note that, technically, a function level static may not necessarily come into existence until the function is first called (and that may make sense for C++ with its constructors) but every C implementation I've ever used creates its function level statics at the same time as file level objects.
Also, whilst I'm using the word "object", I don't mean it in the sense of C++ objects (since this is a C question). It's just because static can apply to variables or functions at file level and I need an all-encompassing word to describe that.

>Function level statics are still used quite a bit - they can cause trouble in multi-threaded programs if that's not catered for but, provided you know what you're doing (or you're not threading), they're the best way to preserve state across multiple function calls while still providing for encapsulation.

>Even with threading, there are tricks you can do in the function (such as allocation of thread specific data within the function) to make it workable without exposing the function internals unnecessarily.

>The only other choices I can think of are global variables and passing a "state variable" to the function each time.

>In both these cases, you expose the inner workings of the function to its clients and make the function dependent on the good behavior of the client (always a risky assumption).

###Pg 84.
3. Register Variables的学习。  
register variables有很大的限制：
	* 只能用在automatic variable中。形式如: 
	<pre><code>
	f(register unsigned m, register char n)
	{j
			register int x;
	}
	</code></pre>
	* 超量使用register variable是没问题的，超出的部分实际并没被存储在register中。
	* register variable的地址是无法被获取的，也就是不能用&操作符来获取地址。 即使实际没用被存在	 register中的 register variable也是不能被获取地址的。
	
###Pg 88.
>这是关于预处理的内容。可以看书了解。不笔记了。

## Chapter 5: Pointers And Arrays
###Pg 94. 
1. &的深入认识。  
&只能获取那些在内存中的变量的地址。例如，variables and array elements(在 data section)。 但是, expressions、 constants(在text section)、register variables是不行的。

2. 关于变量声明和函数声明的另类理解。   
例如 `int *myVar, myFunc(int *);` 表示的是表达示`*myVar`、`myFunc(int *)`有类型为 int的值。

###Pg 99.
3. 关于数组与指针关系描述的几段原话。

>a reference to `a[i]` can also be written as `*(a+i)`.（`*a`就是`a[0]`。） In evaluationg `a[i]`, C converts it to `*(a+i)` immediately, the two forms are equivalent.

>There is one difference between an array name and a pointer that must be kept in mind. A pointer is a variable, so pa=a and pa++ are legal. But an array name is not a variable; constructions like a=pa and a++ are illegal. (Because `a` can't be assigned value.)

>Any operation that can be achieved by array subscripting can also be done with pointers. The pointer version will in general be faster.

>在用指针表示数组时，如果该指针前还有元素，则`p[-2]`等写法是可行的。


###Pg 105.
4. 字符串的结尾	'\0'的特殊用处。   
\0可以用于条件判断，表示false。

###Pg 112.
5.  如何理解多维数组，其与指针的关系如何？  
例如，`daytab[i][j]`可以理解为包含`array[j]`object的一维数组`daytab[i]`。`daytab[i]`中的每个元素都是一个`array[j]`数组的地址。这样方便我们理解`int (*daytab)[13]`,它是指向array[13]的指针。`daytab`是第一个`array[13]`的地址，`daytab+1` 是第二个`array[13]`的地址。这样就可以用来表示二维数组`daytab[2][13]`。

	对于`f(int daytab[2][13])`,`f(int daytab[][13])`,	`f(int (*daytab)[13])`这3申明都是等价的。其中3个daytab的值是相等的。另外，更重要的是，与`f(int *daytab[2])`也是等价的，daytab值也是相等的。其实，如果用图来描述，就会发现daytab本身实际上是同一内容，只是最后该二维数组的表现方式不同而已。
	
	总的来说，该节内容很容易让人迷糊。要多看。书写的很好很清晰。数组指针和指针数组是完全不同的两事。
	
###Pg 114.
6. 对该页的`char *name[]`例子的探究。  
这是一个等式：`name[i][j]=*(*(name+i)+j)=*(name[i]+j)=(*(name+i))[j]`。    
*这里还有些问题很难想通。先放下来。*  

##Chapter 6: Structures
>这章结构体的相关内容。在C#中struct是构造自定义值类型的关键词。又有点象构造'类'。实际上这章开头，作者所说的文字，表明了struct就是一种用于构造新type的工具。

###Pg 131.
1. 访问struct中的元素时，用`.`操作符。如果声明的是指针结构体，则用`->`操作符。
     关于它的优先级别需要弄明白：./-> 操作符优先级大于 * 大于++ 。
     * `++p->len`
     * `(++p)->len`
     * `(p++)->len`==`p++->len` 
     * `*p->str++`
     * `*p++->str`  
     以上内容需要琢磨清楚。
