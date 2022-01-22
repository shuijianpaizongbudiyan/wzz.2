
#include<stdio.h>
int year = 2022;
void test()
{
	printf("test()-- = %d\n", year);
}

int main()
{
	test();
	printf("hello world\n");
	char ch = 'A';
	printf("%c\n",ch);
	short age = 18;
	printf("age = %d\n",age);
	int sum1 = 0;
	int sum2 = 0;
	int sum = 0;
	scanf("%d%d", &sum1, &sum2);
	sum = sum1 + sum2;
	printf("sum = %d\n", sum);
    return 0;
}

int main()
{
	//"abc"默认最后还有结束标志'\0'
	//char arr3没有结束标志，它的长度随机
	//strlen 为字符串长度
	const int n = 10;
	int arr[10] = { 0 };
	char arr1[] =  "abc" ;
	char arr2[] = { 'a','b','c','\0'};
	char arr3[] = { 'a','b','c' };
	printf("arr1 = %s\n", arr1);
	printf("arr2 = %s\n", arr2);
	printf("arr3 = %s\n", arr3);
	printf("%d\n", strlen(arr1));
	printf("%d\n", strlen(arr2));
	printf("%d\n", strlen(arr3));
	return 0;
 }

转义字符
int main()
{
	// \ddd表示八进制，\xdd表示十六进制
	printf("%d\n", strlen("c:\test\32\test.c"));
	printf("%c\n", '\132');
	//  \32表示3，2两个8进制数字，转化为十进制为26，printf出来的是在ASCII码值
	// \为转义字符，要printf ',即printf("%c\n",'\'')
	// \t,\32都作为一个字符
	return 0;
}

if else 语句
int main()
{
	int input = 0;
	printf("加入比特\n");
	printf("你要好好学习吗?>(1/0):");
	scanf("%d", &input);

	if (input == 1)
	{
		printf("你会得到好offer");
	}
	else
	{
		printf("回家卖红薯");
	}
	return 0;
}

函数相加
int Add(int x, int y)
{
	int z = x + y;
	return z;
}
int main()
{
	int a = 520;
	int b = 521;
	int sum = 0;
	sum = Add(a, b);
	printf("sum = %d\n", sum);
	return 0;
}

int main()
{
	//<<左移符，>>右移符
	//整形1占四个字节32个bit,即0*29 001
	int a = 1;
	int b = a << 2;
	printf("%d\n", b);
	//a << 2 相当于0*29 100，结果为4，其实左移x就是乘以二的x次方，右移就是除以二的x次方
	return 0;
}

int main()
{
	int a = 3;
	int b = 5;
	//& = py.and
	//| = py.or
	//^ 同0异1
	//a = 001
	//b = 101
	//a^b = 110 = 6, a&b = 001 = 1
	printf("%d\n", a & b);
	return 0;
}

int main()
{
	int i = 0;
	int arr[10] = { 0 };
	printf("%d\n", sizeof(arr));
	i = (sizeof(arr) / sizeof(arr[0]));
	//数组元素个数 = 数组总个数 / 数组中每个元素大小
	printf("%d\n", i);
	return 0;
}

int Max(int x, int y)
{
	if (x > y)
		return x;
	else
		return y;
}
int main()
{
	int num1 = 12;
	int num2 = 23;
	int max = Max(num1, num2);
	printf("max = %d\n", max);
	return 0;
}

int main()
{
	int a = 10;//先赋值，再++
	//int b = a++;//a = 11,b = 10
	int b = ++a;//a = 11,b = 11
	printf("a = % d  b = % d\n", a, b);
	return 0;
}

int main()
{
	//int a = (int)3.14;//将double转化为int,(类型)
	//假 0
	//真 非0
	int a = 3;
	int b = 5;
	int c = a && b;//&&相当于and,||即or
	printf("c = %d\n", c);
	int max = 0;
	max = (a > b ? a : b);
	printf("max = %d\n", max);
	//exp1? exp2 : exp3 如果exp1为真，返回exp2,反之 三目操作符或者条件操作符
	return 0;
}

int main()
{
	//register int a = 10;//建议把a放入寄存器（处理更快）里，系统会自动根据重不重要来看
	//int 定义的变量是有符号的
	//(signed) int,signed一般省略
	//unsigned int a = -13;它是没有符号的所以a为13
	//typedef 类型定义/类型重定义
	//typedef unsigned int u_int
	//u_int a = -13 和 unsigned int a = -13一模一样
	return 0;
}

//int a = 1;这个位置printf23456
void test()
{
	static int a = 1;//a是一个静态的局部变量
	//int a = 1;
	a++;
	printf("a = %d\n", a);
}
int main()
{
	int i = 0;
	while (i < 5)
	{
		test();
		i++;
	}
	return 0;
}

static 修饰局部变量
局部变量的生命周期变长（变为全局变量）
static 修饰全局变量
改变了全局变量的作用域-只能在自己的源文件内部使用
static修饰函数后失去外部链接属性

int main()
{
	extern int wzz;
	extern int Add(int, int);
	//extern申明外部符号
	printf("wzz = %d\n", wzz);
	int a = 10;
	int b = 20;
	int sum = Add(a, b);
	printf("sum = %d\n", sum);
	return 0;
}

//宏的定义
#define MAX(X,Y) (X > Y? X : Y)
int main()
{
	int a = 10;
	int b = 20;
	int max = MAX(a, b);
	printf("max = %d\n", max);
	return 0;
}

int main()
{
	int a = 10;
	//&a//取a的地址
	printf("%p\n", &a);
	int* p = &a;
	//有一种变量是来存放地址的-指针变量 指针变量的类型为int*
	*p = 20;//* - 解引用操作符
	printf("%p\n", p);
	char ch = 'a';
	char* pc = &ch;
	*pc = 'w';
	printf("%p\n", pc);
	printf("%c\n", ch);
	//指针大小在32位平台是4个字节，在64位是8个字节
	printf("%d\n", sizeof(char *));
	return 0;
}

//结构体
#include<string.h>
struct Book
{
	char name[20];
	short price;
};
int main()
{
	struct Book b1 = { "C语言程序设计",55 };
	struct Book* pd = &b1;
	strcpy(b1.name ,"C++");//name是一个数组，不能直接改，数组名本身上是一个地址
	//strcpy - 字符串拷贝-库函数-string.h
	b1.price = 15;//price是变量，可以直接改
	//pd是一个指针变量，指向的就是b1
	printf("%s\n", pd->name);
	printf("%d\n", pd->price);
	//*pd就是b1，pd存取了b1的地址
	printf("%s\n", (*pd).name);
	printf("%d\n", (*pd).price);
	//.结构体变量.成员
	//->结构体指针->成员
	printf("书名 = %s\n", b1.name);
	printf("价格 = %d\n", b1.price);
	return 0;
}
