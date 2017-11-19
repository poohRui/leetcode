# C++之string

## 简介

简单的说就是字符串类型，使用前引用头文件`#include<string>`，

## 常用方法

### string 转为 char*

使用`str.c_str()`，可以转换为`char*`类型

### char* 转为 string

直接赋值即可转换，即`string str = c`，c为`char*`类型。

### 字符串的连接

可使用`+操作符`或者`append()`，其中`append`方法可接受`char*`和`string`类型的参数。

### 得到字符串的长度

使用`str.length()`方法，返回当前字符串的长度。

### 输入字符串存在空格

当需要控制台输入字符串时，如果输入的字符串中带有空格，只使用普通的`cin`会导致，空格后的内容被忽略，如果想保留完整的字符串，则需要使用`getline(cin,str)`，将输入的字符串(包括空格)保存在`str`中。

### 字符串的子字符串

使用`str.substr(start,len)`方法，表示返回从`start`开始向后数`len`个字符组成的子字符串。

### 字符串某个位置的字符

使用`str.at(index)`方法，如果`index`超过str的长度，则报错，和下标访问类似。





