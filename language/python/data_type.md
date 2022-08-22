# Python数据类型 -- Data Type

## 基本数据类型 -- Basic Type

### int
数字类型，无上限

### str
字符串类型

### bytes
不可变长的字节序列，python2中等价于str

### bytearray
可变长的字节序列

### 列表 -- list
创建实例：`strs = ['str1', 'str2', ...]`  
有序可更改
索引形式：正索引：`strs[1]`、负索引：`strs[-1]`、范围索引：`strs[2:5]`、负范围索引：`strs[-4:-1]`  

### 元组 -- tuple
创建实例：`('str1', 'str2', ...)`  
有序且不可更改  

### 集合 -- set
创建实例：`strs = {'str1', 'str2', ...}`  
无序无索引

### 词典 -- dictionary  
创建实例：`strs = { 'key1' : 'str1', 'key2' : 'str2', ...}`  
无序、可变和有索引  

## 类 -- Custom Class
定义类：
``` Python
class demo_class:
    # constructor method
    def __init__(self):
        pass
    # instance method
    def demo_method(self):
        pass

    # static method
    @staticmethod
    def demo_static_method():
        pass

    # more defined method please search python document
```

## 类型转换 -- Type Convert
@Shooting TODO
