#数据处理#
C++的命名规则：

*	在名称中只能使用字母、数字和下划线*	
*	名称中第一个字符不能是数字
*	区分大小写
*	不能将C++关键字用作名称
*	两个下划线、下划线及大写字母打头的名称被保留给实现，一个下划线开头的名称被保留给实现，用作全局标识符
*	C++对于名称的长度没有限制，ANSI C(C99标准)前63个字符有效

术语宽度用于描述存储整数时使用的内存量

头文件climits中包含了关于整形限制的信息

C++提供了灵活的标准，确保最小长度：

*	short最少16位
*	int至少与short一样长
*	long至少32位，且至少与int一样长

最大的long有10位数

在C++编译过程中，首先将源代码传递给预处理器，对于#define，预处理器查找独立的标记（单独的单词），跳过嵌入的单词

对于被设计成可用于C和C++中的头文件，必须使用#define定义常量

C++确保无符号类型整型变量超出限制，其值将为范围另一端的取值，但不保证符号整型超越限制时不出错

int被设置为对目标计算机而言最为“自然”的长度。自然长度是指计算机处理起来效率最高的长度

如果知道变量可能表示的整数值大于16位整数的最大可能值，则使用long，即使系统上int为32位也应这样做

wchar_t宽字符类型，可表示扩展字符集，可以通过加上前缀L来指示宽字符常量和宽字符串

const限定符：一定要在声明常量时初始化，否则常量的值将不确定并且无法修改

对于浮点数有效位数的要求，float至少32位，double至少48位，且不少于float，long double至少和double一样多，这3种类型的指数范围至少是-37~37

通常：float使用32位内存，double使用64位，long double使用80~128位

%求模，两个操作数必须都是整型，如果其中一个值为负数，则结果的符号依赖于实现

浮点常量在默认情况下为double类型

整型提升：在计算表达式时，C++将bool、char、unsigned char、signed char和short转换为int

如果short比int短，unsigned short转换为int，如果两类型长度相同，unsigned short转换为unsigned int，以确保对unsigned short进行提升时不会损失数据

wchar\_t被提升为下列类型中第一个宽度足够存储wchar\_t取值范围的类型：int、unsigned int、long、unsigned long

编译器转换标准：

*	如果有一个操作数的类型为long double，则另一个操作数转换为long double
*	否则，如果有一个操作类型是double，则将另一个操作数转换为double
*	否则，如果有一个操作数是float，则将另一个操作数转换为float
*	否则执行整型提升
*	如果有一个操作数类型是unsigned long，则将另一个操作数转换为unsigned long
*	否则，如果一个操作数是long int，而另一个是unsigned int，转换取决于两种类型的相对度度，如果long能够表示unsigned int所有可能值，将unsigned int转换为long
*	否则两个都转换为unsigned long
*	否则，如果一个操作数是long，将另一个操作数转换为long
*	否则，如果一个操作数是unsigned int，将另一个操作数转换为unsinged int
*	如果编译器到达此处，说明两个操作数都是int

强制转换的通用格式：

*	C：(typeName) value
*	C++：typeName (value)
*	C++：static_cast<typeName> (value)

