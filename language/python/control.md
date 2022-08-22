# Python控制结构

## 分支结构
if 语句：
``` Python
if bool_sentence1:
    # do something
elif bool_sentence2:
    # do something
else:
    # do something
```

switch 分支：在Python 3.10之前，不支持switch条件分支，但是可以通过字典和lambda表达式实现，
示例如下：  
``` Python
switch = {
    "case1" : lambda a, b : a + b # case 1 do function
    "case2" : lambda a, b : a * b # case 2 do function
}
expression = "case_n"
switch[expression]
```

## 循环结构
使用迭代器的for循环语句：
``` Python
start = 1
end = 10
step = 2
for i in range(start, end, step):
    # do something

demo_list = ['str1', 'str2', ...]
for item in demo_list:
    # do something
```
while循环语句：
``` Python
while bool_sentence:
    # do something
```