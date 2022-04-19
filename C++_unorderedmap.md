---
title: C++ unordered_map使用方法
date: 2022-04-19 16:11:45
tags:
categories: C++
---

# C++ unordered_map使用方法
## 一.什么是unordered_map
unordered_map容器，直译过来就是"无序map容器"的意思。所谓“无序”，指的是unordered_map容器不会像map容器那样对存储的数据进行排序。换句话说，unordered_map容器和map容器仅有一点不同，即map容器中存储的数据是有序的，而unordered_map容器中是无序的。

具体来讲，unordered_map容器和map容器一样，以键值对（pair类型）的形式存储数据，存储的各个键值对的键互不相同且不允许被修改。但由于unordered_map容器底层采用的是哈希表存储结构，该结构本身不具有对数据的排序功能，所以此容器内部不会自行对存储的键值对进行排序。

## 二.常用方法
+ begin() 	返回指向容器中第一个键值对的正向迭代器。
+ end()  	返回指向容器中最后一个键值对之后位置的正向迭代器。
+ empty() 	若容器为空，则返回 true；否则 false。
+ size() 	返回当前容器中存有键值对的个数。
+ max_size() 	返回容器所能容纳键值对的最大个数，不同的操作系统，其返回值亦不相同。
+ operator[key] 	该模板类中重载了 [] 运算符，其功能是可以向访问数组中元素那样，只要给定某个键值对的键 key，就可以获取该键对应的值。注意，如果当前容器中没有以 key 为键的键值对，则其会使用该键向当前容器中插入一个新键值对。
+ at(key) 	返回容器中存储的键 key 对应的值，如果 key 不存在，则会抛出 out_of_range 异常。 
+ find(key) 	查找以 key 为键的键值对，如果找到，则返回一个指向该键值对的正向迭代器；反之，则返回一个指向容器中最后一个键值对之后位置的迭代器（如果 end() 方法返回的迭代器）。
+ count(key) 	在容器中查找以 key 键的键值对的个数。
+ emplace() 	向容器中添加新键值对，效率比 insert() 方法高。
+ emplace_hint() 	向容器中添加新键值对，效率比 insert() 方法高。
+ insert()  	向容器中添加新键值对。
+ erase() 	删除指定键值对。
+ clear()  	清空容器，即删除容器中存储的所有键值对。
+ swap() 	交换 2 个 unordered_map 容器存储的键值对，前提是必须保证这 2 个容器的类型完全相等。
+ hash_function() 	返回当前容器使用的哈希函数对象。

## 三.初始化
```C++
std::unordered_map<std::string, std::string> umap;//构造一个 <string,string> 类型键值对的 unordered_map 容器,下同
unordered_map<string,sting> umap;
```