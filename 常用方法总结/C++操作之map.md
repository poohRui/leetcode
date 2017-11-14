# C++操作之map

## 简介

关联式存储数据的容器，由`(key,value)`键值对组成，`key(键值)`作为排序和唯一区别容器内元素的标志，`value`值可以修改但`key`值一经确定不能修改。

内部采用效率很高的`红黑树`实现，可以看成是一种特殊的二叉查找树，所以查找某一个键，插入和删除的效率基本都为`log(n)`。

## 常用方法

### 声明

`map<key_type,value_type> map_name`

### 插入

可以直接采用下标插入

`map_name[key] = value;`

### 查找

`map<key_type,value_type>::iterator it = map_name.find(search_key);`

最终`it == map_name.end()`表示没有找到

### 遍历

* 声明迭代器

  `map<key_type,value_type>::iterator it=map_name.begin()`

* 循环遍历结束条件`it!=map_name.end()`

* 输出容器中的键值对

  `it->first,it->second`

* 也可以用`for`循环，使用下标访问

### 删除

* `map_name.erase(key)`根据键值删除

* `map_name.erase(it)`用迭代器删除

* `map_name.erase(map_name.begin(),`

  `map_name.end())`删除范围内的所有元素。

