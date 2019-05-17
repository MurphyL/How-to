---
description: Java容器
---

![Java容器](./puml/java-collections.svg)

## 门面接口

### 基础接口

```java
interface Iterable<T> {

    Iterator<T> iterator()

}

interface Map<K,V> {

    int size()
    boolean isEmpty()

    boolean containsKey(Object key)
    boolean containsValue(Object value)
    
    V get(Object key)
    V put(K key, V value)
    V remove(Object key)
    
    void putAll(Map<? extends K, ? extends V> m)
    
    void clear()
    
    Set<K> keySet()
    Collection<V> values()
    Set<Map.Entry<K, V>> entrySet()

}
```

### 主要容器接口

```java
interface Collection<E> extends Iterable<E> {

    int size()
    boolean isEmpty()

    boolean contains(Object o)
    boolean containsAll(Collection<?> c)

    boolean add(E e)
    boolean addAll(Collection<? extends E> c)
    boolean remove(Object o)
    void clear()

    boolean retainAll(Collection<?> c)

    Object[] toArray()
    <T> T[] toArray(T[] a)

}

interface Queue<E> extends Collection {

    boolean offer(E e)
    E poll()
    E element()
    E peek()

}

interface Deque<E> extends Queue {

    void addFirst(E e)
    void addLast(E e)

    boolean offerFirst(E e)
    boolean offerLast(E e)

    E removeFirst()
    E removeLast()

    E pollFirst()
    E pollLast()

    E getFirst()
    E getLast()

    E peekFirst()
    E peekLast()

}
```

## 主要容器

### Queue（`PriorityQueue`）

#### PriorityQueue


### List（`ArrayList`、`LinkedList`）


{% hint style="warn" %}
** 和数组的主要区别 **：数组的长度难以扩充，数组中数据的类型必须相同。
{% endhint %}

#### ArrayList

#### LinkedList

### Set（`TreeSet`、`HashSet`、`LinkedHashSet`）

Set集合中不区分元素的顺序，不允许出现重复的元素（用户自定义的类有的时候需要实现相应方法），相同的元素不会被加入。


#### TreeSet

{% hint style="info" %}
TreeSet容器特殊，元素放进去的时候自然而然就有顺序。
{% endhint %}

#### HashSet

#### LinkedHashSet

### Map（`HashMap`、`TreeMap`、`Hashtable`）

{% hint style="info" %}
 没有继承java.util.Collection接口。
{% endhint %}

#### HashMap



#### TreeMap

#### Hashtable



## 工具类

### Collections

Collections 工具类常用方法:

1. 排序
2. 查找，替换操作
3. 构造不可变容器

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
 * 旋转
 * 当distance为正数时，将list中的后distance个元素整体移到前面；
 * 当distance为负数时，将list中的前distance个元素整体移到后面。
 */
void rotate(List list, int distance)
/**
 * 对list进行二分查找，返回索引，注意list必须是有序的
 */
int binarySearch(List list, Object key)
/**
 * 根据元素的自然顺序，返回最大的元素。 类比int min(Collection coll)
 */
int max(Collection coll)W
/**
 * 用指定的元素代替指定list中的所有元素
 */
void fill(List list, Object obj)
/**
 * 统计元素出现次数
 */
int frequency(Collection c, Object o)
/**
 * 构造空容器（类比List、Map）
 */
<T> T emptySet()
/**
 * 构造单值（只有一个元素）容器（类比Set、Map）
 */
<T> T singletonList()
/**
 * 构造不可变容器（类比Set、List）
 */
<T> T unmodifiableMap()
```
