---
title: C++ vector使用方法
date: 2022-04-13 16:10:14
tags:
categories: C++
---
# C++ vector使用方法
## 一、什么是vector
    向量（Vector）是一个能够存放任意类型的动态数组。

## 二、特性
### 1.顺序序列

    顺序容器中的元素按照严格的线性顺序排序。可以通过元素在序列中的位置访问对应的元素。
### 2.动态数组

    支持对序列中的任意元素进行快速直接访问，甚至可以通过指针算述进行该操作。操供了在序列末尾相对快速地添加/删除元素的操作。

## 三、基本函数实现
+ void push_back(const T& x)​:向量尾部增加一个元素X
+ void pop_back()​:删除向量中最后一个元素
+ ​void clear()​:清空向量中所有元素
+ bool empty() const​:判断向量是否为空，若为空，则向量中无元素
+ int size() const​:返回向量中元素的个数
+  int capacity() const​:返回当前向量所能容纳的最大元素值
+ int max_size() const​:返回最大可允许的 vector 元素数量值
+ void swap(vector&)​:交换两个同类型向量的数据
+ void assign(int n,const T& x)​:设置向量中前n个元素的值为x
+ void assign(const_iterator first,const_iterator last)​:向量中[first,last)中元素设置成当前向量元素

## 四、基本用法
 `#include < vector>`
 `using namespace std;`
+ Vector<类型>标识符
+ Vector<类型>标识符(最大容量)
+ Vector<类型>标识符(最大容量,初始所有值)

## 五、基本操作
    (1)头文件​#include<vector>​.

    (2)创建vector对象，​vector<int> vec​;

    (3)尾部插入数字：​vec.push_back(a)​;

    (4)使用下标访问元素，​cout<<vec[0]<<endl​;记住下标是从0开始的。

    (5)使用迭代器访问元素.

```C++
    vector<int>::iterator it;
    for(it=vec.begin();it!=vec.end();it++)
        cout<<*it<<endl;
```

    (6)插入元素：​vec.insert(vec.begin()+i,a)​; 在第i+1个元素前面插入a;

    (7)删除元素：​vec.erase(vec.begin()+2)​ ; 删除第3个元素; vec.erase(vec.begin()+i,vec.end()+j)​; 删除区间[ i,j-1] 区间从0开始;

    (8)向量大小: ​vec.size()​;

    (9)清空: ​vec.clear()​;

    特别提示：这里有 begin() 与 end() 函数、front() 与 back() 的差别