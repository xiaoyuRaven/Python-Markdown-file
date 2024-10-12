@[TOC](printf 和 scanf)
***
# 一、printf
## 1. printf的基本用法
`printf()`的作用是将参数文本输出到屏幕上，`printf`中的`f`代表`format`（格式化），表示可以定制输出文本的数据。

```c
#include <stdio.h>

int main()
{
	printf("hello world");
	return 0;
}
```
上面命令会在屏幕上输出一行文字“hello world”。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2822eca478b14146a84d0f6af5b80da1.png#pic_left)

printf()不会在行尾自动添加换行符，运行结束后，光标就停留在输出结束的地方，不会自动换行。为了让光标移动到下一行的开头，可以在输出文本的结尾添加一个换行符`\n`。如果文本的内部有换行也可以通过插入换行符来实现。

```c
#include <stdio.h>

int main()
{
    printf("hello world\n");//'\n'换行
	return 0;
}
```
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/b8090941150645db95c76c0b14186396.png#pic_left)

```c
#include <stdio.h>

int main()
{
	printf("abc\ndef"); //'\n'换行
	return 0;
}
```
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/647afccd23a14a70a35e0de9b1a5086f.png#pic_left)
`printf()`是在标准库的头文件`stdio.h`定义的，使用这个函数之前，必须要在源码文件头部引入这个头文件。

## 2. 占位符
占位符的这个位置可以被其他值取代。
`printf()`可以在输出文本中指定占位符。

```c
#include <stdio.h>

int main()
{
	printf("%d\n", 100);
	printf("%dabc\n", 100);
	
	printf("%s will come tonight\n", "lisi");
	//%s will come tonight\n是输出文本，字符串代替占位符%s

	printf("%s says that it is %d o'clock\n","lisi",10); 
	//'%s says that it is %d o'clock\n','lisi','10'是printf()的三个参数
	//printf()的参数个数=占位符个数+1
	
	return 0;
}
```

 - 占位符的第一个字符一律是百分号`%`,第二个字符表示占位符的类型，例如`%d`表示这里替代的值必须是整数。
 - 输出文本中可以使用多个占位符
 - `printf()`参数和占位符是一一对应的，如果有==n==个占位符，`printf()`的参数就应该是==n+1==个。如果参数的个数少于对应的占位符，`printf()`可能会输出内存中的任意值。

## 3. 常见的占位符

> %a ：十六进制浮点数，字母输出为小写。 
> %A ：十六进制浮点数，字母输出为大写。 
> %c ：字符。 
> %d ：⼗进制整数。 **// int**
> %e ：使⽤科学计数法的浮点数，指数部分的 e 为⼩写。 
> %E ：使⽤科学计数法的浮点数，指数部分的 E 为⼤写。 
> %i ：整数，基本等同于%d 。
> %f ：小数（包含 float 类型和 double 类型）。 **//float - %f ，double - %lf**
> %g ：6个有效数字的浮点数。整数部分⼀旦超过6位，就会⾃动转为科学计数法，指数部分的 e为⼩写。 
> %G ：等同于%g，唯⼀的区别是指数部分的 E 为⼤写。 
> %hd ：十进制 short int 类型。 
> %ho ：八进制 short int 类型。 
> %hx ：⼗六进制 short int 类型。
> %hu ：unsigned short int 类型。 
> %ld ：⼗进制 long int类型。
> %lo ：⼋进制 long int 类型。 
> %lx ：⼗六进制 long int 类型。 
> %lu ：unsigned long int 类型。 
> %lld ：⼗进制 long long int 类型。
> %llo ：⼋进制 long long int 类型。 
> %llx ：⼗六进制 long long int 类型。 
> %llu ：unsigned long long int 类型。 
> %Le：科学计数法表⽰的 long double 类型浮点数。 
> %Lf ：long double 类型浮点数。
> %n ：已输出的字符串数量。该占位符本⾝不输出，只将值存储在指定变量之中。
> %o ：⼋进制整数。
> %p ：指针（⽤来打印地址）。
> %s ：字符串。
> %u ：⽆符号整数（unsigned int）。
> %x ：⼗六进制整数。
> %zd ： size_t 类型。
> %% ：输出⼀个百分号。


一个简单的代码例子如下：
```c
#include <stdio.h>

int main()
{
	printf("this is %c\n", 'A');
	printf("%hd\n", 100);
	printf("%ho\n", 100);
	printf("%x\n", 15);
	return 0;
}
```

## 4. 输出格式
`printf()`可以定制占位符的输出格式。
## 5. 限定占位符的最小宽度
`printf()`允许限定占位符的最小宽度。
### 5.1 对于整数限定最小宽度
用`%md`表示这个占位符的最小宽度为m位，输出的值默认为右对齐，如果输出的值不满m位，对应的值前面会添加空格。如果希望改成左对齐，在输出内容的后面添加空格，需要在占位符`%`的后面插入一个`-`号（负号）。如果输出的内容超过m位，就会打印出全部内容。

```c
#include <stdio.h>

int main()
{
	printf("%d\n", 123);
	printf("%5d\n", 123);//输出右对齐
	printf("%-5dxxx\n", 123);//输出左对齐
	printf("%5d\n", 12345);
	printf("%5d\n", 123456);
	return 0;
}
```
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c499d8c2170744c99b1a8e30571db36c.png#pic_left)
### 5.2 对于小数限定最小宽度
对于小数，这个限定符会限制所有数字的最小显示宽度。（小数的默认显示精度是小数带你后六位）

```c
#include <stdio.h>

int main()
{
	printf("%lf\n", 123.45);
	//%f和%lf在打印的时候小数点后，默认时打印六位的
	printf("%12lf\n", 123.45);
	printf("%-12lfxxx\n", 123.45);
	return 0;
}
```
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/83372f8e8e6d4570a95f950a47a85ef8.png#pic_left)
### 5.2 限定小数点后的小数位数
想要保留小数点后m位，占位符可以写成`%.mf`或者`%.mlf`。保留精确后的结果时遵循四舍五入的原则，限定小数位数超过参数内容的小数位的情况下，补0达到限定小数位数。

```c
#include <stdio.h>

int main()
{
	printf("%lf\n", 123.45);
	printf("%.0lf\n", 123.45);
	printf("%.1lf\n", 123.45);
	printf("%.2lf\n", 123.45);
	printf("%.3lf\n", 123.45);
	printf("%.4lf\n", 123.45);
	printf("%.5lf\n", 123.45);
	printf("%.6lf\n", 123.45);
	printf("%.7lf\n", 123.45);
	printf("%.8lf\n", 123.45);
	return 0;
}
```
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/bc61bfe710314ab5b04924e68d9c5a9c.png#pic_left)
### 5.3 既限定打印数值的最小宽度又限定小数点后的位数

```c
#include<stdio.h>

int main()
{
	printf("%8.1lf\n", 123.45);
	printf("%4.0lf\n", 123.45);
	printf("%3.0lf\n", 123.45);
	printf("%12.2lf\n", 123.45);
	printf("%-4.0lfxxx\n", 123.45); //加上xxx更直观
	printf("%lf\n", 123.45);
	return 0;
}
```
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/ce8ddb3e88bd4766bd32c99572746e65.png#pic_left)
在这里从输出结果的逻辑上来讲，是先根据小数位数的限定精确保留小数位，再根据限定数值的最小宽度，确定最终打印结果。（==这个是个人观点==）
#### 5.3.1 `*`代替限定值
最小宽度和小数位数这连个限定值，都可以用`*`代替，通过`printf()`的参数传入。

```c
#include <stdio.h>

int main()
{
	printf("%12.1lf\n", 123.45);
	printf("%*.*lf\n", 12, 1, 123.45);
	return 0;
}
```
上面示例中，`%*.*lf`的两个`*`通过`printf()`的连个参数`12`和`1`传入。
### 5.4 输出内容总是显示正负号
默认情况下，`printf()`不对正数显⽰`+`号，只对负数显示`-`号。如果想让正数也输出`+` 号，可以在占位符的`%`后面加⼀个 `+` 。

```c
#include <stdio.h>

int main()
{
	printf("%d\n", 123);
	printf("%d\n", -123);
	printf("%+d\n", 123);
	printf("%+d\n", -123);
	return 0;
}
```
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/b6836d951d704515bace72dca99c7044.png#pic_left)
### 5.5 输出部分字符串
`%s`占位符用来输出字符串，默认是全部输出。如果只想输出开头的部分，可以用`%.[m]s` 指定输出的长度，其中`[m]`代表⼀个数字，表示所要输出的长度。

```c
#include <stdio.h>

int main()
{
	printf("%s\n", "abcdef");
	printf("%.0s xxx\n", "abcdef");
	printf("%.1s\n", "abcdef");
	printf("%.2s\n", "abcdef");
	printf("%.3s\n", "abcdef");
	printf("%.4s\n", "abcdef");
	printf("%.5s\n", "abcdef");
	printf("%.6s\n", "abcdef");
	printf("%.7s xxx\n", "abcdef");
	return 0;
}
```
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5c9daefed75e409b88307901b1f686b7.png#pic_left)
# 二、scanf
当我们有了变量，我们需要给变量输⼊值就可以使用`scanf`函数，如果需要将变量的值输出在屏幕上的时候可以使用`prinf`函数。

```c
#include <stdio.h>

int main()
{
	int score = 0;

	printf("请输入成绩:");
	scanf("%d", &score);//输入操作
	//scanf函数中占位符的后边的参数需要的是地址
	//& 是取地址操作符，&score — 取出score的地址

	printf("成绩是：%d\n", score);
	return 0;
}
```
原理图示如下：
（==标准输入一般指的是键盘，标准输出一般指的是屏幕==）
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/0aef66decfaa4c9d96816efecf1414b3.png#pic_left)
## 1. scanf的基本用法
`scanf()` 函数用于读取用户的键盘输入，程序运行到这个语句时，会停下来，等待用户从键盘输⼊，用户输入数据并按下回车键后，`scanf()` 就会处理用户的输入，将其存入量。
`scanf`函数的原型定义在头文件`stdio.h`中，它的语法形式与`printf`函数的语法形式类似。

```c
scanf("%d", &i);
```
`scanf()`的第一个参数`%d`，表示用户输入的是一个整数。`%d`就是一个占位符，`%`是占位符的标志，`d`表示整数。第二个参数`&i`表示将用户从键盘输入的整数存入变量`i`。
C语言的数据都是有类型的，`scanf()`必须提前知道用户输入的数据类型，才能处理数据，它的第一个参数是一个格式字符串，里面会放置占位符，(该占位符与`printf()`的占位符基本一致)，告诉编译器如何解读用户的输入，需要提取的数据类型。它的其余参数是存放用户输入的变量的，格式字符串里面有多少个占位符，就有多少个变量。
==注意==：变量的前面必须加上`&`（数组、指针变量除外），因为`scanf()`传递的不是值，而是地址，即将变量`i`的地址指向用户输入的值。
### 1.1 一次输入多个变量

```c
#include <stdio.h>

int main()
{
	int a = 0;
	int b = 0;
	float f1 = 0.0;
	float f2 = 0.0;
	scanf("%d %d %f %f", &a, &b, &f1, &f2); 
	printf("%d %d %f %f\n", a, b, f1, f2);
	return 0;
}
```
`scanf()`处理数值占位符时，会自动过滤空白字符，包括空格、制表符、换行符等。所以，用户输入的数据之间，有⼀个或多个空格不影响`scanf()`解读数据。另外，用户使用回车键，将输入分成几行，也不影响解读。
`scanf()`处理用户输入的原理是，用户的输入先放入缓存，等到按下回车键后，按照占位符对缓存进行解读。解读用户输入时，会从上一次解读遗留的第一个字符开始，直到读完缓存，或者遇到第一个不符合条件的字符为止。

```c
#include <stdio.h>

int main()
{
	int x;
	float y; //浮点数在内存中有可能无法精确保存（后续讲解）

	// ⽤⼾输⼊ " -13.45e12# 0"
	scanf("%d", &x);
	printf("%d\n", x);
	scanf("%f", &y);
	printf("%f\n", y);
	return 0；
}
```
`scanf()`读取用户输入时，`%d`占位符会忽略起首的空格，从`-`处开始获取数据，读取到 `-13`停下来，因为后面的 . 不属于整数的有效字符。这就是说，占位符`%d`会读到`-13`。第⼆次调用`scanf()`时，就会从上⼀次停止解读的地方，继续往下读取。这一次读取的首字符是`.`，由于对应的占位符是`%f`，会读取到`.45e12`，这是采用科学计数法的浮点数格式。后面的不属于浮点数的有效字符，所以会停在这里。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5c2aae0326ff47be8952d1a3ebb81c49.png#pic_left)
浮点型数据之所以有上图输出结果，原因是因为0.45无法在内存中精确的保存。
由于`scanf()`可以连续处理多个占位符，所以上面的代码可以改写：

```c
#include <stdio.h>

int main()
{
	int x;
	float y; //浮点数在内存中有可能无法精确保存（后续讲解）
	scanf("%d %f", &x, &y);//scanf可以处理多个占位符
	printf("%d %f\n", x, y);
	return 0;
}
```
### 1.2 输入格式
`scanf`的参数输入格式一定要正确（匹配）。

```c
#include <stdio.h>

int main()
{
	int a = 0;
	int b = 0;
	/*scanf("%d %d", &a, &b);*/
	scanf("%d,%d", &a, &b);
	printf("%d %d\n", a, b);
	return 0;
}
```
因为在`scanf`中两个占位符之间有`,`，在输入参数时，两个参数之间也要加上`,`，否则输出不了想要的结果。


## 2. scanf的返回值

- `scanf()` 的返回值是⼀个整数，表示成功读取的变量个数。
- 如果没有读取任何项，或者匹配失败，则返回 0 。
- 如果在成功读取任何数据之前，发生了读取错误或者遇到读取到文件结尾，则返回常量 EOF (-1)。(==EOF - end of file ⽂件结束标志==)

```c
#include <stdio.h>

int main()
{
	int a = 0;
	int b = 0;
	int c = 0;
	int d = 0;
	int ret = scanf("%d %d %d %d", &a, &b, &c,&d);
	printf("a=%d b=%d c=%d d=%d\n", a, b, c, d);
	printf("ret = %d\n", ret);
	return 0;
}
```
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/e8a02308d6fe479c8da0e73779894aae.png#pic_left)
在VS2022中要想提前结束输入，需要换行按三次`ctrl+z`，才能提前结束输入。（以输入两个参数后提前结束输入为例），只成功读取了连个数据，所以`scanf`的返回值是2。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8381fb199bf847f7b8e7f399b4fdab8d.png#pic_left)
如果一个参数不输入，按三次`ctrl+z`，结果输出的`ret`是`-1`，也就是`EOF`。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/6ca34a5741154fec9eeacd7bec80d8ff.png#pic_left)
## 3. 占位符
`scanf()`的常用占位符如下：

> - %c ：字符。
> - %d ：整数。
> - %f ： float 类型浮点数。
> - %lf ： double 类型浮点数。
> - %Lf ： long double 类型浮点数。
> - %s ：字符串。
> - %[] ：在方括号中指定⼀组匹配的字符（比如 %[0-9] ），遇到不在集合之中的字符，匹配将会停止。

上面所有占位符之中，**除了 `%c` 以外，都会自动忽略起首的空白字符**。 `%c` 不忽略空白字符，总是返回当前第⼀个字符，无论该字符是否为空格。如果要强制跳过字符前的空白字符，可以写成 `scanf(" %c", &ch)` ，即 `%c` 前加上⼀个空格，表示跳过零个或多个空白字符。
**特别说⼀下占位符`%s`**，它其实不能简单地等同于字符串。它的规则是，从当前第⼀个⾮空⽩字符开始读起，直到遇到空⽩字符（即空格、换⾏符、制表符等）为止。因为`%s`不会包含空白字符，所以无法用来读取多个单词，除非多个`%s`⼀起使用。这也意味着，`scanf()`不适合读取可能包含空格的字符串，比如书名或歌曲名。另外`scanf()`遇到`%s`占位符，会在字符串变量末尾存储⼀个空字符 `\0` 。
`scanf()` 将字符串读入字符数组时，不会检测字符串是否超过了数组长度。所以，储存字符串时，很可能会超过数组的边界，导致预想不到的结果。为了防止这种情况，使用`%s` 占位符时，应该指定读入字符串的最长长度，即写成 `%[m]s` ，其中的 `[m]` 是⼀个整数，表示读取字符串的最大长度，后面的字符将被丢弃。

```c
#include <stdio.h>

int main()
{
	char arr[5] = { 0 };//数组
	//scanf("%s", arr);  
	//不限制读入字符串的长度，如果读取的长度超过数组的长度，编译器会报错
	//arr是数组名，数组名就是地址，不需要加取地址操作符
	scanf("%4s", arr);
	//%[m]s ，其中的 [m] 是⼀个整数，表⽰读取字符串的最⼤⻓度，后⾯的字符将被丢弃
	printf("%s\n", arr);
	return 0;
}
```
`scanf()`的占位符`%4s`表示最多读取用户输入的4个字符，后面的字符将被丢弃，这样就不会有数据溢出的风险。

## 4. 赋值忽略符 - `*`
有时用户的输入可能不符合预定的格式

```c
#include <stdio.h>

int main()
{
	int year = 0;
	int month = 0;
	int day = 0;
	scanf("%d-%d-%d", &year, &month, &day);
	printf("%d %d %d\n", year, month, day);
	return 0;
}
```
以上代码，如果用户输入`2024-10-1`，就能正确解读出年、月、日，但是用户可能输入其他的格式例如`2024\10\1`，在这种情况下，`scanf`解析数据就会失败。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4c57e1facf8c4f2ca17564020d279ed3.png#pic_left)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c237610faad34bfa894332a5fdb4d067.png#pic_left)
用`scanf()`提供的**赋值忽略符** - `*`就能解决上述问题，只要把`*`加在任何占位符的百分号后面，该占位符就不会返回值，解析后将被丢弃。

```c
#include <stdio.h>

int main()
{
	int year = 0;
	int month = 0;
	int day = 0;
	scanf("%d%*c%d%*c%d", &year, &month, &day);
	//scanf("%d%*s%d%*s%d", &year, &month, &day);
	//在这里个人觉得还是尽量不要用%*s，原因是因为%s的规则是，从当前第⼀个非空白字符开始读起，直到遇到空白字符（即空格、换⾏符、制表符等）为止，比%*c复杂，输入格式上要求更高
	printf("%d %d %d\n", year, month, day);
	return 0;
}
```
上面示例中， `%*c` 就是在占位符的百分号后⾯，加⼊了赋值忽略符 - `*` ，表示这个占位符没有对应的变量，解读后不必返回。