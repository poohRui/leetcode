# C++之vector

## 简介

是一种类数组的顺序存储容器，可以动态的改变容器的大小，随着元素的加入，其内部会自动扩容。使用前引用头文件`#include<vector>`，

## 常用方法

### 声明

```c++
vector<type> vec;
```

### 在最后添加元素

```C++
vec.push_back(item);
```

### 弹出最后一个元素

！该方法没有`return`值，并不会把弹出的元素返回

```C++
vec.pop_back();
```

### 遍历

* 可以使用下标进行遍历

* 可以使用迭代器进行遍历

  ```c++
  vector<type>::iterator it = vec.begin();
  while(it != vec.end()){
    //do something
    cout<<*it<<endl;
    it++;
  }
  ```

### 容器大小

```c++
int size = vec.size();
```

#### 删除元素

可删除某个元素，或者某个范围内的所有元素，删除元素的位置使用迭代器表示。

```c++
vector<type>::iterator it = vec.begin();
vec.erase(it);//删除第一个元素
vec.erase(it,it+3);//[it,it+3)内的所有元素
```

### 内存释放

在一些程序中如果不释放内存，会产生严重的内存泄露问题，单单使用`vec.clear()`不能起到释放内存的作用，可以使用`swap`方法来帮助释放内存。

```C++
vector<type>().swap(vec);
```







