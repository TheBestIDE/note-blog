# C数据类型 -- Data Type

## 基本数据类型 -- Basic Type

### 空类型 -- `void`  
版本：ANSI C  

<br/>

### 整型
**1. `char`**  
版本：ANSI C  
占用空间：1字节  

**2. `short`**  
版本：ANSI C  
占用空间：2字节  

**3. `int`**  
版本：ANSI C  
占用空间：4字节  

**4. `long`**    
版本：ANSI C  
占用空间：8字节  

<br/>

### 浮点型
**1. `float`**      
版本：ANSI C  
单精度浮点数  
占用空间：4字节  
浮点数标准：IEEE 754
浮点数格式：  
| 符号位 S | 阶码 e   | 尾数 f  |
| ------- | ------- | ------ |
| 31      | 30 - 23 | 22 - 0 |

真值表：  
| Value Typye | S      | e           | f      | Value                     |
| ----------- | ------ | ----------- | ------ | ------------------------- |
| +0          | 0      | 0           | 0      | 0                         |
| -0          | 1      | 0           | 0      | -0                        |
| +&infin;    | 0      | 255(All 1)  | 0      | &infin;                   |
| -&infin;    | 1      | 255(All 1)  | 0      | -&infin;                  |
| NaN         | 0 or 1 | 255(All 1)  | &ne;0  | NaN                       |
| 规格化非0正数 | 0      | 0 < e < 255 | f      | 2<sup>e - 127</sup>(1.f)  |
| 规格化非0负数 | 1      | 0 < e < 255 | f      | -2<sup>e - 127</sup>(1.f) |
| 非规格化正数  | 0      | 0           | f&ne;0 | 2<sup>-126</sup>(0.f)     |
| 非规格化负数  | 1      | 0           | f&ne;0 | -2<sup>-126</sup>(0.f)    |
<br/>

**2. `double`**    
版本：ANSI C  
双精度浮点数  
占用空间：8字节  
浮点数标准：IEEE 754    
浮点数格式：  
| 符号位 S | 阶码 e   | 尾数 f  |
| ------- | ------- | ------ |
| 63      | 62 - 52 | 51 - 0 |
真值表：  
| Value Typye | S      | e            | f      | Value                      |
| ----------- | ------ | ------------ | ------ | -------------------------- |
| +0          | 0      | 0            | 0      | 0                          |
| -0          | 1      | 0            | 0      | -0                         |
| +&infin;    | 0      | 2047(All 1)  | 0      | &infin;                    |
| -&infin;    | 1      | 2047(All 1)  | 0      | -&infin;                   |
| NaN         | 0 or 1 | 2047(All 1)  | &ne;0  | NaN                        |
| 规格化非0正数 | 0      | 0 < e < 2047 | f      | 2<sup>e - 1023</sup>(1.f)  |
| 规格化非0负数 | 1      | 0 < e < 2047 | f      | -2<sup>e - 1023</sup>(1.f) |
| 非规格化正数  | 0      | 0            | f&ne;0 | 2<sup>-1022</sup>(0.f)     |
| 非规格化负数  | 1      | 0            | f&ne;0 | -2<sup>-1022</sup>(0.f)    |

<br/>

### 指针
**1. 一般指针**    


**2. 数组指针**    
``` C
(void* []) ptr;
```

**3. 指针数组**    
``` C
(void*)ptr [];
```

**4. 函数指针**    
``` C
void (*ptr)(int, int); // 指向函数签名 void function(int var1, int var2);
```

**5. 空指针 -- `void*`**  
可以存储所有指针类型  
**示例**  
``` C
typedef int (*fptr)(int, int);

int function(int x, int y) {
    return x + y;
} 

int example() {
    void* p = function;
    return ((fptr)p)(4, 10);
}
```

<br/>

## 自定义数据类型 -- Custom Type

### 结构体 -- `struct`
版本：ANSI C  
作用：将相关的数据类型聚集成集合，内存分配时按照内存对齐进行相关处理。  
**示例**  
``` C
struct student1 {
    char name[45];
    int id;
}

struct student2 {
    int id;
    char name[45];
}
```  
对于`struct student1`类型，由于`int`类型占4字节，根据内存对齐原则，其内存起始地址为4的倍数，故内存占用空间为：(45 + 3 + 4) = 52，`name`成员和`id`成员中的3字节无法被访问。  
对于`struct student2`类型，`char`类型占1字节，根据内存对齐原则，其内存起始地址为1的倍数，故内存占用空间为：(4 + 45) = 49。  

### 联合体 -- `union`
版本：ANSI C  
作用：将多个数据共用同一块内存空间以节省空间。  

### 枚举类型 -- `enum`  
版本：ANSI C
作用：枚举，其实际值为整型  

<br/>

## 类型修饰符 -- Type Modifier

### 作用域类型修饰符
**1. `static`**  
版本：ANSI C  
作用：声明变量为静态变量，在离开函数后不释放空间。  

**2. `auto`**  
版本：ANSI C  
作用：声明变量为自动变量，在离开函数后释放空间。  

**3. `register`**   
版本：ANSI C  
作用：声明变量为寄存器类型，显式声明变量为保存在寄存器中，寄存器变量可能不存放在内存中，所以不能用`&`来取址。  

**4. `extern`**  
版本：ANSI C  
作用：声明变量或函数是在其它文件或本文件的其他位置定义。  

<br/>

### 符号类型修饰符
**1. `signed`**  
版本：ANSI C  
作用：声明变量是有符号数。  

**2. `unsigned`**  
版本：ANSI C  
作用：声明变量是无符号数。  

<br/>

### 其他类型修饰符
**1. `const`**  
版本：ANSI C  
作用：声明只读变量。  
**示例**  
``` C
// 常量指针，其地址指向的内容为常量，即char* p1为常量
const char *p1;
// 指针常量，变量存储的地址为常量，即(*p2)为常量
char const *p2;
```

**2. `volatile`**  
版本：ANSI C  
作用：确保本条指令不会因编译器的优化而省略，且要求每次直接读值。  
**示例**  
对于计算某个整数平方的函数：  
``` C
int square(volatile int *ptr) {
    return ((*ptr) * (*ptr))
}
```
编译器会产生的代码：  
``` C
int square(volatile int *ptr) {
    int a, b;
    a = *ptr;
    b = *ptr;
    return a * b;
}
```
因此要实现该逻辑，代码实现应该为：  
``` C
int square(volatile int *ptr) {
    int a;
    a = *ptr;
    return a * a;
}
```

**3. `typedef`**  
版本：ANSI C  
作用：用于定义类型别名  
常用技巧：  
**简化声明函数指针**  
``` C
#include <stdio.h>

typedef int(fptr*)(int, int);

int operator1(int left, int right) {
    return left + right;
}

int operator2(int left, int right) {
    return left - right;
}

int function(int left, int right, fptr foperator) {
    return foperator(left, right);
}

int main(int args, char* argv[]) {
    int a = 10, b = 20, ret1, ret2;
    ret1 = function(a, b, operator1);
    ret2 = function(a, b, operator2);
    printf("ret1[%d], ret2[%d].\n", ret1, ret2);
    return 0;
}
```

<br/>
