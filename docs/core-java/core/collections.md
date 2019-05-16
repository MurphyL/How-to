---
description: Java集合
---

## List

## Set

## Map

{% hint style="warn" %}
 没有继承java.util.Collection接口。
{% endhint %}

## Collections 工具类和 Arrays 工具类常见方法

Collections 工具类常用方法:

1. 排序
2. 查找,替换操作

```java
/**
 * 反转
 */
void reverse(List list)
/**
 * 随机排序
 */
void shuffle(List list)
/**
 * 按自然排序的升序排序
 */
void sort(List list)
/**
 * 定制排序，由Comparator控制排序逻辑
 */
void sort(List list, Comparator c)
/**
 * 交换两个索引位置的元素
 */
void swap(List list, int i , int j)
/**
 * 旋转。当distance为正数时，将list后distance个元素整体移到前面；
 * 当distance为负数时，将 list的前distance个元素整体移到后面。
 */
void rotate(List list, int distance)
```

## 参考文档

[JavaGuide - 容器](https://github.com/Snailclimb/JavaGuide#%E5%AE%B9%E5%99%A8)

