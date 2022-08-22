# Python调用C动态链接库

**Python标准模块：ctypes**  
**Python版本：2.5及以上**  

## 调用方法：
``` Python
from ctypes import *
# cdecl
dll = cdll.LoadLibrary(dllpath) # dllpath 是c动态库的路径
# stdcall
dll = windll.LoadLibrary(dllpath)
# from ordinal
dll = cdll.kernel32(ordinal)    # ordinal是动态库函数序号
```
<br/>

## 类型对应：
| ctypes 类型    | C 类型                                   | Python 类型                 |
| -------------- | --------------------------------------- | ---------------------------|
| c_char         | char                                    | 1-character string         |
| c_wchar        | wchar_t                                 | 1-character unicode string |
| c_byte         | char                                    | int/long                   |
| c_ubyte        | unsigned char                           | int/long                   |
| c_bool         | bool                                    | bool                       |
| c_short        | short                                   | int/long                   |
| c_ushort       | unsigned short                          | int/long                   |
| c_int          | int                                     | int/long                   |
| c_uint         | unsigned int                            | int/long                   |
| c_long         | long                                    | int/long                   |
| c_ulong        | unsigned long                           | int/long                   |
| c_longlong     | __int64 or longlong                     | int/long                   |
| c_ulonglong    | unsigned __int64 or unsigned long long  | int/long                   |
| c_float        | float                                   | float                      |
| c_double       | double                                  | float                      |
| c_longdouble   | long double float                       | float                      |
| c_char_p       | char *                                  | string or None             |
| c_wchar_p      | wchar_t *                               | unicode or None            |
| c_void_p       | void *                                  | int/long or None           |

<br/>

## 参数类型设置：
```Python
fun.argtypes = (c_int, c_int,c_int,c_void_p) #设置函数参数类型为 int,int,int,void *
fun.restype  = c_float #设置返回值类型为 float
```
<br/>

## 结构体对应关系：
C结构体：
``` C
struct mem_buffer {
    int len;
    int caps;
    char* buffer;
}
```
Python对应的类定义：
``` Python
from ctypes import *

class mem_buffer(Structure):
    _fields_ = [('len', c_int),
                ('caps', c_int),
                ('buffer', POINTER(c_char))]
```

注意事项：对于对应字符串的C类型char*，使用c_char_p对应指针；
对于对应二进制序列的C类型char*，使用POINTER(c_char)对应指针。
c_char_p指针会将字符'\0'认为是字符串结尾。  
<br/>

