# C控制结构 -- Control

## 顺序结构 -- sequence  
**`goto`关键字**  
无条件跳转语句，等同于汇编的`jmp`指令。  
结构化程序设计时，尽量避免使用`goto`语句，以免造成程序流程的混乱，使理解和调试程序都产生困难。  
<br/>

## 分支结构 -- branch
**1. `if` - `else`**  
用法：  
``` C
if (bool_value)
    // do something
else if (bool_value)
    // do something
else
    // do something
```

**2. `switch` - `case`**  
用法：  
``` C
switch (integer_value) {
case integer1:
    // do something if interger_value == integer1
    break;
case integer2:
    // do something if interger_value == integer2
    break;
default:
    // do something if no match
    break;
}
```

<br/>

## 循环结构 -- loop
**1. `for`**  
用法：
``` C
int i;
for (i = 0; i < n; i++) {
    // do something
    if (bool_value1)
        continue;   // goto next loop
    // do something
    if (bool_value2)
        break;      // jump out of loop 
    // do something
}
```
等价于：  
``` C
int i;
i = 0;
while (1) {
    if (i < n)
        break;

    // do something
    if (bool_value1)
        goto END;
    // do something
    if (bool_value2)
        break;      // jump out of loop 
    // do something

END:
    i++;
}
```

**2. `while`**  
用法：  
``` C
while (bool_value) {
    // do something
}
```


**3. `do` - `while`**  
用法：  
``` C
do {
    // do something
} while (bool_value);
```
等价于：  
``` C
while (1) {
    // do something

    if (bool_value)
        break;
}
```

<br/>