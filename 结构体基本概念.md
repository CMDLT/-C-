#### 结构体基本概念

```C
//struct 结构体关键字 Stu - 结构体标签 struct Stu - 结构体类型
struct Stu
{
	//成员变量
	char name[20];
	short age;
	char tele[12];
	char sex[5];
}s1,s2,s3;//s1,s2,s3是三个全局的结构变量

int main()
{
	struct Stu s;//s 是局部的结构体变量
	
	return 0;
}
```
> 全局的结构体变量工作中非迫不得已不要用

#### 结构体重命名

```C
typedef struct Stu
{
	//成员变量
	char name[20];
	short age;
	char tele[12];
	char sex[5];
}Stu;//struct Stu的别名，类型

int main()
{
	struct Stu s1;
	Stu s2;
	return 0;
}
```

#### 结构体变量的初始化

```C
typedef struct Stu
{
	//成员变量
	char name[20];
	short age;
	char tele[12];
	char sex[5];
}Stu;//struct Stu的别名

int main()
{
	struct Stu s1 = {"张三", 20, 1321344145, "男"};
	Stu s2 = {"李思", 18, 18987667890, "女"};
	return 0;
}
```

#### 结构体做结构体的成员变量

```C
#include <stdio.h>

struct S
{
	int a;
	char c;
	char arr[20];
	double d;
};

struct T
{
	char ch[10];
	struct S s;//结构体成员变量
	char *pc;
};

int main()
{
	char arr[] = "hello bit";
	struct T t = {"hehe", {100, 'w', "hello world", 3.14}, arr};//嵌套结构体初始化
	printf("%s\n", t.ch);//hehe
	printf("%s\n", t.s.arr);//hello world
	printf("%1f\n", t.s.d);//3.140000
	printf("%s\n", t.pc);//hello bit
	return 0;
}
```

#### 结构体传参

```C
#include <stdio.h>

typedef struct Stu
{
	//成员变量
	char name[20];
	short age;
	char tele[12];
	char sex[5];
}Stu;//struct Stu的别名

Print1(Stu tmp)
{
	printf("name = %s\n", tmp.name);//张三
}

Print2(Stu* ps)
{
	printf("name = %s\n", ps->name);
}

int main()
{
	struct Stu s = {"张三", 20, 1321344145, "男"};
	Print1(s);//传结构体
	Print2(&s);//传地址
	return 0;
}
```
**注意：**
结构体传参中，Print1和Print2哪个更好？
答：Print2。
原因：如果传输的结构体过大，Print1会占用很多空间，导致空间浪费。
但Print2是传地址只会占用4个字节。
> 函数传参时，参数是需要压栈的，如果传递一个结构体对象的时候，结构体过大，参数压栈的系统开销比较大，所以导致性能下降。

课外可以研究->函数栈帧的创建和销毁
栈
插入一个元素：压栈
删除一个元素：出栈






