#使用类
操作符重载

    operator op (argument-list);

限制：

1. 重载后的操作符必须至少有一个操作数是用户定义的类型
2. 使用操作符时不能违反操作符原来的句法规则
3. 不能定义新的操作符
4. 不能重载以下操作符：
	*	sizeof
	*	.
	*	.*
	*	::
	*	?:
	*	typeid
	*	const_cast
	*	dynamic_cast
	*	reinterpret_cast
	*	static_cast
5. 以下操作符**只能**通过成员函数进行重载
	*	=
	*	()
	*	[]
	*	->

友元：

*	友元函数
*	友元类
*	友元成员函数

通过让函数成为类的友元，可以赋予该函数与类的成员函数相同的访问权限

友元函数：

将其元型放在类声明中，并在元型声明前加上关键字friend：

    friend Time operator* (double m, const Time & t);

编写函数定义，不使用friend关键字，不使用作用域解析操作符

    Time operator* (double m, const Time & t)
    {
        Time result;
        long totalminutes = t.hours * mult * 60 + t.minutes * mult;
        result.hours = totalminutes / 60;
        result.minutes = totalminutes % 60;
        return result;
    }

非成员版本的重载操作符函数所需的形参数目与操作符使用的操作数数目相同；

成员版本所需的参数数目少一个，因为其中的一个操作数是被隐式地传递的调用对象

类的自动转换:

只有接受一个参数的构造函数才能作为转换函数

可以使用关键字explicit关闭隐式转换

隐式转换场景：

-	初始化
-	赋值
-	作为入参传入
-	作为返回值返回时试图返回其他类型值

应谨慎地使用隐式转换函数，通常，最好选择仅在被显式地调用时才被执行的函数

转换函数：

    operator typeName();
    operator int();//转换为int类型

-	转换函数必须是类方法
-	不能指定返回类型
-	不能有参数

全局变量在main()函数被调用之前创建，可以创建一个类，其默认构造函数将调用所有的bootstrap（引导程序）函数

    class CompileRequirements
    {
        private:
        public:
        CompileRequirements()
        {
            GetDataFromSales();
            GetDataFromManufacturing();
            GetDataFromFinance();
        }
    };

    CompileRequirements Req;

    int main(void)
    {
        BuildScheduleFromReq();
    }