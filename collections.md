# Java 集合

Java 2 之前，Java 为对象组的存储和操作提供了特别的类比如 字典，向量，堆栈和属性。尽管这些类确实有用，它们缺少一个中心的，统一的主题。因此，你使用向量的方法和你使用属性的方法是不同的。  

集合框架被设计来满足几个目标 
- 框架需要是高性能的。基础集合(动态数组，链表，数和哈希表)是高效的。  
- 框架需要允许不同的集合类型以类似的方式和高度的互操作性工作。  
- 扩展或者调整集合必须是简单的。  

为此，整个集合框架被设计围绕一系列的标准接口。几个接口的标准实现例如 LinkedList, HashSet 和 TreeSet 被提供，如果你选择的话，你可以使用，你也可以实现你自己的集合。  

一个集合框架是一个统一的体系结构表示和操作集合。所有的集合框架包含以下:  
- **接口:** 这些是代表集合的抽象数据类型。接口允许集合独立操作它们表示的细节。在面向对象的语言中，接口通常形成一个层次结构。  
- **实现,即类：** 这些是集合接口的具体实施。从本质上说，它们是可重用的数据结构。  
- **算法:** 这些是在实现集合接口的对象上进行有用计算的方法，比如搜索和排序。算法被称为多态的，那就是说，同一个方法能被用在许多不同的合适的集合接口的实现上。  

除了集合，框架定义了几个 map 接口和类 Maps 存储键值对。尽管 maps 不是正确使用集合的术语，但是他们完全由集合整合起来。  

## Collection 接口

集合框架定义了几个接口。如下提供了每个接口的概览:  

|SN      |接口描述   |
|----------|:----------:|-----:|
|1 |[Collection 接口](http://www.tutorialspoint.com/java/java_collection_interface.htm)<br> 这让你可以使用对象组；它是集合层次阶段的顶端|
|2 |[List 接口](http://www.tutorialspoint.com/java/java_list_interface.htm)<br> 它继承了 Collection 并且 List 的一个实例存储了元素的一个有序集合|
|3 |[Set](http://www.tutorialspoint.com/java/java_set_interface.htm)<br> 它继承了 Collection 来处理集，它必须含有特殊的元素|
|4 |[SortedSet](http://www.tutorialspoint.com/java/java_sortedset_interface.htm)<br> 它继承了 Set 来处理 排序的 set|
|5 |[Map](http://www.tutorialspoint.com/java/java_map_interface.htm)<br> 它将独特的键和值匹配|
|6 |[Map Entry](http://www.tutorialspoint.com/java/java_mapentry_interface.htm)<br> 这描述了映射中的一个元素(一个键值对)。它是 Map 的一个内部类。|
|7 |[SortedMap](http://www.tutorialspoint.com/java/java_sortedmap_interface.htm)<br> 它继承了 Map 因此键按升序保持|
|8 |[Enumeration](http://www.tutorialspoint.com/java/java_enumeration_interface.htm)<br> 它是旧有的接口并定义了你可以在对象的集合中列举(一次获得一个)元素的方法。这个旧有的接口被迭代器取代了。|
    
## Collection 类

Java 提供了一系列的实现集合接口的标准集合类。一些类提供了完全的能被直接使用的实现，其他就是抽象类，提供的被用来作为创建具体集合的实现。  

标准的 collection 类在下面的表格中被概括:  

|SN      |类描述   |
|----------|:----------:|-----:|
|1 |**AbstractCollection**<br> 实现大部分的 Collection 接口|
|2 |**AbstractList**<br> 继承 AbstractCollection 并且实现大部分 List 接口|
|3 |**AbstractSequentialList**<br>  通过一个使用有序的而不是随机访问它的元素的集合继承  AbstractList|
|4 |[LinkedList](http://www.tutorialspoint.com/java/java_linkedlist_class.htm)<br> 通过继承 AbstractSequentialList 实现一个链表|
|5 |[ArrayList](http://www.tutorialspoint.com/java/java_arraylist_class.htm) <br> 通过继承 AbstractList 实现一个动态数组|
|6 |**AbstractSet**<br> 继承 AbstractCollection 并实现大部分的 Set 接口|
|7 |[HashSet](http://www.tutorialspoint.com/java/java_hashset_class.htm)<br> 用一个哈希表继承 AbstractSet |
|8 |[LinkedHashSet](http://www.tutorialspoint.com/java/java_linkedhashset_class.htm)<br> 继承 HashSet 来允许插入顺序迭代|
|9 |[TreeSet](http://www.tutorialspoint.com/java/java_treeset_class.htm)<br> 实现在树中存储的一个集。继承 AbstractSet|
|10 |**AbstractMap**<br> 实现大部分的 Map 接口|
|11 |[HashMap](http://www.tutorialspoint.com/java/java_hashmap_class.htm)<br> 用一个哈希表继承 AbstractMap|
|12 |[TreeMap](http://www.tutorialspoint.com/java/java_treemap_class.htm)<br> 用一棵树继承 AbstractMap|
|13 |[WeakHashMap](http://www.tutorialspoint.com/java/java_weakhashmap_class.htm)<br> 用一个使用弱键的哈希表来继承 AbstractMap|
|14 |[LinkedHashMap](http://www.tutorialspoint.com/java/java_linkedhashmap_class.htm)<br> 继承 AbstractMap 来允许插入顺序迭代|
|15 |[IdentityHashMap](http://www.tutorialspoint.com/java/java_identityhashmap_class.htm)<br> 继承 AbstractMap 类并且当比较文档时平等使用参考|

AbstractCollection, AbstractSet, AbstractList, AbstractSequentialList 和 AbstractMap 类提供了核心集合接口的实现，尽量减少努力来实现它们。  

以下的由 java.util 定义的旧有的类在前面的指南中已经被讨论过: 

|SN      |类描述   |
|----------|:----------:|-----:|
|1 |[Vector](http://www.tutorialspoint.com/java/java_vector_class.htm)<br> 这实现一个动态数组。它和 ArrayList 类似，但也有一些不同。|
|2 |[Stack](http://www.tutorialspoint.com/java/java_stack_class.htm)<br> Stack 是 Vector 的实现标准的后进先出栈的子类
|3 |[Dictionary](http://www.tutorialspoint.com/java/java_dictionary_class.htm)Dictionary<br>  是一个抽象的代表一个键值对存储库的类并且操作起来非常像 Map|
|4 |[Hashtable](http://www.tutorialspoint.com/java/java_hashtable_class.htm)<br> Hashtable 是初始的 java.util 的一部分并且是 Dictionary 的具体实现|
|5 |[Properties](http://www.tutorialspoint.com/java/java_properties_class.htm)<br> Properties 是 Hashtable 的一个子类。它被用来保持键是一个字符串并且值也是一个字符串的值的列表|
|6 |[BitSet](http://www.tutorialspoint.com/java/java_bitset_class.htm)<br> 一个 BitSet 类创建一个特殊的保持 bit 数值的数组类型。这个数组的大小能根据需要增长|

## Collection 算法

集合框架定义了几个能被应用到 collections 和 maps 的算法。这些算法在 Collection 类的内部被定义为静态方法。  

几个方法能抛出异常 **ClassCastException**，它发生在想要比较不兼容的类型时；或者异常**UnsupportedOperationException**，它发生在想要修改一个不能修改的集合时。  

集合定义了三个静态变量：EMPTY_SET, EMPTY_LIST, 和 EMPTY_MAP。所有都是不变的。

|SN      |算法描述   |
|----------|:----------:|-----:|
|1 |[The Collection Algorithms](http://www.tutorialspoint.com/java/java_collection_algorithms.htm)<br> 这是所有算法实现的列表|

## 如何使用 Iterator

通常，你想要在集合中循环元素。比如，你可能想要显示每个元素。  

这么做最简单的方法是使用 Iterator，它是一个实现或者是 Iterator 或者 ListIterator 接口的对象。  

Iterator 让你可以通过一个集合循环，获得或者除去元素。ListIterator 继承了 Iterator 来允许一个列表的双向遍历和元素的修改。

|SN      |Iterator 方法描述   |
|----------|:----------:|-----:|
|1 |[使用 Java Iterator](http://www.tutorialspoint.com/java/java_using_iterator.htm)<br> 这是所有由 Iterator 和 ListIterator 接口提供的有例子的方法的列表。|

## 如何使用 Comparator

TreeSet 和 TreeMap 都以顺序保存元素。然而，是 Comparator 精确定义排序意味着什么。  

这个接口让我们将一个给定的集合用不同数量的方法排序。这个接口也能被用来排列任何类的任何实例(甚至是我们不能修改的类)。  

|SN      |Iterator 方法描述   |
|----------|:----------:|-----:|
|1 |[使用 Java Comparator](http://www.tutorialspoint.com/java/java_using_comparator.htm)<br> 这是所有由 Comparator 接口提供的有例子的方法的列表。|

## 总结

Java 集合框架给了程序员打包数据结构和操作它们的算法的入口。 

一个集合是一个能对其他对象引用的对象。collection 接口声明了能在每一个集合类型上操作的操作。  

集合框架的类和接口都在 java.util 包内。