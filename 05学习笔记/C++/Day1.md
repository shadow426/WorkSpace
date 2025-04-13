
markdown随便写写

# 标题
## 二级标题
###### 六级标题
井号+空格+标题内容


1. 列表
2. 有序列表
3. 数字+'.'+空格
	1. 多层缩进
		1. 普通缩进+Tab
4. 结束


- 无序列表
- ‘-’+空格
	- 多层缩进，普通缩进+Tab


这是没有加粗的文字
**这是加粗之后的文字**
**"\*\*"+内容+"\*\*"**
__也可以这样写__
**”__“+内容+”__“**


这是正常的文字
*这是斜体的文字*
*"\*"+"内容"+”\*“*
_也可以这样写_
*"\_"+"内容"+”\_“*



**插入图片**

使用方法:\!\[图片名称]\(图片链接)
例:
![Engelbart](https://history-computer.com/ModernComputer/Basis/images/Engelbart.jpg)



**改变图片大小**

使用方法:\!\[图片名称|图片大小](图片链接)
例:
![Engelbart|100](https://history-computer.com/ModernComputer/Basis/images/Engelbart.jpg)

`一行的代码块`
反引号\`+一行的代码内容+反引号\`

```
多行代码块
三个反引号```
内容
三个反引号```

```


%%行内注释%%


%%
多行注释
所谓注释就是只显示在编辑模式，不显示在预览
%%

~~删除线~~
\~\~删除线\~\~

### 1.C++概述
1. C++两大编程思想
	1. 面向对象
	2. 泛型编程
2. 移植性和标准
	1. ANSI 在1998制定出C++第一套标准  C++98
	2. 2011年  C++11
3. C++编程方式，融合了三种编程方式
	- C语言代表过程性的语言
	- 面向对象
	- 泛型编程

其他一些点
- C++是C的超集，任何有效的C程序都是有效的C++程序



```
// 没有.h
#include <iostream>

using namespace std;	// 使用  标准  命名空间

//#include <time.h>
//#include <ctime>     //c++用c的库

int main()
{
	// << 左移用于在cout后拼接输出的内容
	// endl  end line  刷新缓冲区  然后换行  在win里\r\n  在Linux里\n  使用endl即可统一
	cout << "Hello World\n" << 123 << endl
		;
	return 0;
}
```




### 2.C++初始

1. 引入头文件  \#include \<iostream\> 标准输入输出流
2. 使用标准命名空间   using  namespace  std;
3. 标准输出流对象 cout << “..” << 1234 << 3.14 << endl;
4. 面向对象三大特性
	1. 封装、继承、多态


```
#define _CRI_SECURE_ND_WARNINGS

#include <iostream>

//using namespace std;

int atk = 1000;

void test01()
{
	int atk = 2000;
	std::cout << "atk = " << atk << std::endl;
	// ::代表作用域  如果前面什么都没添加代表全局作用域
	std::cout << "全局 atk = " << ::atk << std::endl;
}


int main()
{
    std::cout << "Hello World!\n";
	test01();
}


//输出结果为
Hello World!
atk = 2000
全局 atk = 1000

```

### 3.双冒号作用域运算符

1. ::代表作用域  如果前面什么都不添加 代表全局作用域

```
#include <iostream>
#include "game1.h"
#include "game2.h"

using namespace std;


// 1.命名空间用途：解决名称冲突
void test01()
{
	KingGlory::goAtk();
	LOL::goAtk();
}


// 2.命名空间下 可以放 变量、函数、结构体、类...
namespace A
{
	int m_A;
	void func();
	struct MyStruct
	{

	};
	class Animal
	{

	};

}

// 3.命名空间必须声明在全局作用域下
void test02()
{
	//namespace B
	//{ }
}


// 4.命名空间可以嵌套命名空间
namespace B
{
	int m_A = 10;
	namespace C
	{
		int m_A = 20;
	}
}

void test03()
{
	cout << "B空间下的m_A" << B::m_A << endl;
	cout << "C空间下的m_A" << B::C::m_A << endl;
}


// 5.命名空间是开放的，随时可以添加新成员 合并不是覆盖
namespace B
{
	int m_B = 15;
}

void test04()
{
	cout << "B空间下的m_A = " << B::m_A << endl;
	cout << "B空间下的m_B = " << B::m_B << endl;
}


// 6.命名空间可以是匿名的
namespace
{
	int m_C = 1000;
	int m_D = 2000;
	// 当写的命名空间匿名时，相当于写了 static int m_C = 1000,static int m_D = 2000;
}

void test05()
{
	cout << "m_C" << m_C << endl;
	cout << "m_D" << ::m_D << endl;
}

//7.命名空间可以起别名
namespace veryLongName
{
	int m_E = 10000;
}

void test06()
{
	namespace veryShortName = veryLongName;
	cout << "m_E = " << veryShortName::m_E << endl;
	cout << "m_E = " << veryLongName::m_E << endl;
}

int main()
{
	test01();
	test02();
	test03();
	test04();
	test05();
	test06();
    std::cout << "Hello World!\n";
}

//运行结果
王者荣耀攻击方式
LOL攻击方式
B空间下的m_A10
C空间下的m_A20  
B空间下的m_A = 10
B空间下的m_B = 15
m_C1000
m_D2000
m_E = 10000
m_E = 10000
Hello World!

```

```
//game1.h

#pragma once
#include <iostream>

using namespace std;

// 还能这么玩
namespace KingGlory
{
	void goAtk();
}

```

```
//game1.c
#include "game1.h"

void KingGlory::goAtk()
{
	cout << "王者荣耀攻击方式" << endl;
}
```

```
//game2.h

#pragma once
#include <iostream>

using namespace std;

namespace LOL
{
	void goAtk();
}


```

```
//game2.c

#include "game2.h"

void LOL::goAtk()
{
	cout << "LOL攻击方式" << endl;
}

```


### 4.namespace命名空间

1.代码同3
 1. 命名空间用途：解决名称冲突
 2. 命名空间下可以存放 ： 变量、函数、结构体、类…
 3. 命名空间必须要声明在全局作用域
 4. 命名空间可以嵌套命名空
 5. 命名空间是开放的，可以随时将新成员添加到命名空间下
 6. 命名空间可以匿名的
 7. 命名空间可以起别名


### 5.using声明以及using编译指令

1. using声明
	1. using KingGlory::sunwukongId
	2. 当using声明与 就近原则同时出现，出错，尽量避免
2. using编译指令
	1. using namespace KingGlory;
	2. 当using编译指令  与  就近原则同时出现，优先使用就近
	3. 当using编译指令有多个，需要加作用域 区分

```
#include <iostream>
using namespace std;

namespace KingGlory
{
	int sunwukongId = 1;
}

void test01()
{
	int sunwukongId = 2;

	//1. using声明
	//using KingGlory::sunwukongId;

	// 当using声明与 就近原则同时出现，出错，尽量避免
	// 报错 多次声明
	cout << sunwukongId << endl;

}

void test02()
{
	int sunwukongId = 2;
	// 2.using编译指令
	// 相当于打开一个房间用里面的变量，与就近原则冲突时，使用就近原则
	using namespace KingGlory;
	//当using编译指令有多个，需要加作用域区分
	cout << sunwukongId << endl;
}

int main()
{
	//test01();
	test02();
    std::cout << "Hello World!\n";
}

运行结果
2
Hello World!
```


### 6.C++对C语言增强以及扩展

1. 全局变量检测增强
	1.  int a ;
	2. int a = 10;  C下可以，C++重定义
2. 函数检测增强
	1. 函数的返回值
	2. 形参类型
	3. 函数调用参数个数
3. 类型转换检测增强
	1. char * p = (char \*)malloc(64)  C++下必须等号左右一致类型
4. struct 增强
	1. C++可以在结构体中放函数
	2. 创建结构体变量   可以简化关键字struct
5. bool数据类型扩展
	1. C++才有bool类型
	2. 代表真 --- 1 true  假 ---- 0 false
	3. sizeof  = 1
6. 三目运算符增强
	1. C语言下返回的是值
	2. C++语言下返回的是变量
7. const增强
	1. C语言下
		1. 全局const   直接修改 失败  间接修改  语法通过，运行失败
		2. 局部 const  直接修改  失败  间接修改  成功
	2. C++语言下
		1. 局部 const  直接修改失败   间接修改 失败  
		2. C++const可以称为常量


**第6点不太明白**
**第7点const增强不太明白**



```
//C语言

#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

// 1.全局变量检测增强
int a;
int a = 10;

// 2.函数检测增强 返回值没有检测  形参类型没有检测  函数调用参数个数没有检测
getRects(w, h)
{
	return w * h;
}

void test01()
{
	printf("%d\n",getRects(10,20,30));
}

// 3.类型转换检测增强
void test02()
{
	char * p = malloc(64);
}

// 4.struct增强
struct Person
{
	int age;
	// C语言下结构体不可以有函数
	//void func();
};

// 5.booll类型扩展 C语言下没有这个类型
//bool b;	//bool类型 代表真假

void test03()
{
	struct Person p; //创建结构体变量时候，必须加关键字struct
	p.age = 100;
}

// 6.三目运算符增强
void test04()
{
	int a = 10;
	int b = 20;

	printf("ret = %d\n", a > b ? a : b);

	//a > b ? a : b = 100;	//C语言下 返回的是值 20 = 10
	*(a > b ? &a : &b) = 100;
	printf("a = %d\n", a);
	printf("b = %d\n", b);

}

//7.const增强
//全局const
const int m_A = 100;  //受到常量区保护，运行修改失败

void test05()
{
	//m_A = 200;
	//int *p = &m_A;
	//*p = 200;

	//局部const
	const int m_B = 100;	//分配到栈上
	//m_B = 200;

	int *p = &m_B;
	*p = 200;

	printf("%d\n", m_B);

	//int arr[m_B];  //在C语言下，const是伪常量，不可以初始化数组
}

int main()
{
	test01();
	test02();
	test03();
	test04();
	test05();
	return 0;
}


运行结果
200
ret = 20
a = 10
b = 100
200

```

```
//C++语言

#include <iostream>

using namespace std;

// 1.全局变量检测增强 C++检测出重定义
//int a;
int a = 100;

// 2.函数检测增强 返回值有检测  形参类型有检测  函数调用参数个数有检测
int getRects(int w, int h)
{
	return w * h;
}

// 3.类型转换检测增强,必须得加强制转换
void test02()
{
	char * p = (char *)malloc(64);
}

void test01()
{
	printf("%d\n", getRects(10, 20));
}


// 4.struct增强
struct Person
{
	int age;
	// C++语言可以有函数
	void func()
	{
		age++;
	}
};

void test03()
{
	Person p; //创建结构体变量时候，可以不加关键字struct
	p.age = 100;
	p.func();
	cout << p.age << endl;
}

// 5.booll类型扩展 C语言下没有这个类型
bool flag;	//bool类型 代表真假

void test04()
{
	cout << sizeof(flag) << endl;
	flag = true;
	flag = 100;	// 将非零的数都转换为1
	cout << flag << endl;
}

// 6.三目运算符增强
void test05()
{
	int a = 10;
	int b = 20;

	printf("ret = %d\n", a > b ? a : b);

	//(a > b ? a : b) = 100;	//C++语言下 返回的是变量 b = 100
	// 返回还是a = 10  b = 20 ，b = 100是一起的
	a < b ? a : b = 100;

	printf("a = %d\n", a);
	printf("b = %d\n", b);

}

//7.const增强
// 全局const
const int m_A = 100;	//和C语言结论一致

void test06()
{
	//m_A = 200;
	//int *p = (int *)&m_A;
	//*p = 200;

	//局部const
	//在c++里有符号表 键值对 m_B->100
	const int m_B = 100;
	//m_B = 200;

	//执行下面这行代码时候相当于 修改temp的值
	//int temp = m_B
	//int *p = (int *)&m_B;
	int *p = (int *)&m_B;
	*p = 200;
	cout << "m_B = " << m_B << endl;
	int arr[m_B];	// C++下const修饰的变量称为常量，可以初始化数组

}

int main()
{
	test01();
	test02();
	test03();
	test04();
	test05();
	test06();
    std::cout << "Hello World!\n"; 
}


运行结果
200
101
1
1
ret = 20
a = 10
b = 20
m_B = 100
Hello World!

```


### 7.const 链接属性

1. C语言下const修饰的全局变量默认是外部链接属性
2. C++下const修饰的全局变量默认是内部链接属性，可以加extern 提高作用域


```
//C语言
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

//外部链接属性是什么意思

int main()
{
	//链接阶段
	extern const int g_a;
	printf("g_a = %d\n", g_a);
	return 0;
}

运行结果
g_a = 1000
```

```
//test.c
const int g_a = 1000;
```





```
//C++语言
#include <iostream>
using namespace std;
int main()
{
	extern const int g_b;
	
	cout << "g_b = " << g_b << endl;
    std::cout << "Hello World!\n";
}
运行结果
g_b = 1000
Hello World!
```

```
//test.c
extern const int g_b = 1000;//默认是内部链接属性 可以加关键字extern提作用域  C语言隐式加extern
```


### 8.const分配内存情况

1. 对const变量 取地址 ，会分配临时内存  
2. 使用普通变量  初始化 const变量
3. 对于自定义数据类型

```
#include <iostream>
#include <string>

using namespace std;

//1.对const变量取地址，会分配临时内存，间接修改修改不了
//使用常量修改，修改不了
void test01()
{
	const int a = 10;
	int * p = (int *)&a;
	*p = 20;
}


//2.使用普通变量初始化const变量，修改成功
//
void test02()
{
	int a = 10;
	const int b = a;

	//为什么使用变量初始化就可以修改
	//直接用数字赋值时，编译阶段可能会优化为常量
	//用变量初始化时，运行时b的值才确定所以不会优化;
	int * p = (int *)&b;
	*p = 30;
	cout << "b = " << b << endl;
}

//3.对于自定义数据类型 可以间接修改
struct Person
{
	string m_Name;
	int m_Age;
};

void test03()
{
	const Person p;
	//p.m_Age=20;

	Person *pp = (Person *)&p;
	(*pp).m_Name = "Tom";
	pp->m_Age = 10;

	cout << "姓名 = " << p.m_Name << "年龄 = " << p.m_Age << endl;
}

int main()
{
	test01();
	test02();
	test03();

    std::cout << "Hello World!\n";
}
```

### 9.尽量用const代替define

1. define出的宏常量，没有数据类型、不重视作用域

- 1.const有类型，可以进行编译器类型安全检查。
- 2.const有作用域，而#define不重视作用域

#undefine 卸载宏


### 10.引用

```
#include <iostream>

using namespace std;

//1.引用基本语法，类型  &别名 = 原名
//类型必须一样
void test01()
{
	int a = 10;
	int &b = a;

	b = 100;
	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
}

//2.注意事项
void test02()
{
	int a = 10;
	//int &b;//1.错误，引用必须要初始化
	int &b = a;
	int c = 100;
	b = c;// 赋值，不能重新引用
	
	cout << a << endl;
	cout << b << endl;
	cout << c << endl;
}

//3.对数组建立引用
void test03()
{

	cout << "test03" << endl;
	//1.直接建立引用
	int arr[10];
	int(&pArr)[10] = arr;

	for (int i = 0; i < 10; i++)
	{
		arr[i] = 100 + i;
	}
	for (int i = 0; i < 10; i++)
	{
		cout << pArr[i] << endl;
	}

	//2.先定义数组类型，再通过类型定义引用
	typedef int(ARRAY_TYPE)[10];
	ARRAY_TYPE & pArr2 = arr;

	for (int i = 0; i < 10; i++)
	{
		cout << pArr2[i] << endl;
	}
}

int main()
{
	int a = 10;
	int &b = a;	// 目的，起别名
	test01();
	test02();
	test03();
    std::cout << "Hello World!\n";
}
```



引用
&等号右边取地址  等号左边是引用




关于左值与右值
### **左值和右值**

1. **左值（Lvalue）**：
    
    - 左值是一个表达式，它指向一个具体的内存位置。
        
    - 左值可以出现在赋值操作的左侧。
        
    - 例如：变量、数组元素、解引用指针等。
        
2. **右值（Rvalue）**：
    
    - 右值是一个临时值，它没有持久的内存地址。
        
    - 右值不能出现在赋值操作的左侧。
        
    - 例如：字面量、临时对象、表达式的结果等。


**函数返回引用时**：

- 当函数返回引用时，返回值是一个左值，因为它指向某个具体的内存位置（通常是某个变量或对象）。
    
- 因此，函数调用表达式可以作为左值，出现在赋值操作的左侧。


**函数返回值（非引用）时**：

- 当函数返回值（非引用）时，返回值是一个右值，它是一个临时值，没有持久的内存地址。
    
- 因此，函数调用表达式不能作为左值，不能出现在赋值操作的左侧。





关于返回值
- **返回非引用类型**：返回的是值的副本。
    
- **返回引用类型**：返回的是变量的引用。
    
- **返回指针类型**：返回的是指针的值（内存地址）。



### 引用的本质
实现一个指针常量
int & aRef = a;  自动转换为int * const aRef = &a  这也能说明引用必须初始化，指针常量必须初始化
aRef = 20  内部发现是引用，自动转化为\*aRef = 20


所以必须初始化，指针常量必须初始化

指向一个地址之后无法改