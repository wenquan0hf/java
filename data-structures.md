# Java 数据结构

Java 工具包中所提供的数据结构非常强大并且有很多的功能。这些数据结构包含以下的接口和类：

- Enumeration
- BitSet
- Vector
- Stack
- Dictionary
- Hashtable
- Properties

现在这些类都是旧的了， Java-2 已经引入了一种新的框架叫做 Collections Framework，在下一个章节中来讲解它。

##  Enumeration

枚举接口本身并不是一个数据结构，但是它在其他数据结构中非常重要。 The Enumeration 接口定义了一种方法可以从一个数据结构中连续获取元素。

例如，Enumeration 定义了一个叫做 nextElement 的方法，它可以用来在一个包含很多元素的数据结构中获得下一个元素。 

## BitSet

BitSet 类实现了一组 bits 或 flags，可以被独立的设置和清除。

在你需要保存一组布尔值的时候这个类非常有用；你只需要给每个值或集合赋值一个 bit 并且可以视情况设置或清除它。

## Vector

Vector 类和传统的 Java 数组类似，但是它可以增添新的元素。

和数组一样，Vector 对象的元素可以通过下标序号来访问。

对于使用 Vector 类很好的是,在创建的时候不用担心去设置一个特定的集合大小;当必要的时候,它可以自动收缩和扩张。

## Stack

Stack 类中的元素后进先出（LIFO）。

你可以简单认为 stack 就是一个对象的垂直堆栈；当你添加一个新元素的时候，它就位于其它元素的顶部。

当你将一个元素移出 stack，从栈的顶部开始移出。换句话说，加进栈的最后一个元素会被最先移除。

## Dictionary

Dictionary 类是一个定义了键值对映射这种数据结构的抽象类。

当你想通过一个特殊的键来访问数据而不是通过一个整数下标时最好使用 Dictionary 这个类。

因为 Dictionary 类是抽象的，它只提供了键值对映射的数据结构框架而不是一个具体的实现。

## Hashtable

Hashtable 类提供了一种组织数据的方式，依赖于一些用户自定义的键。

例如，在一个地址列表的 hash table 中，你可以依赖于像 ZIP code 这种键来存储和排序数据而不是依赖于一个人的名字。

在 hash table 中键的特殊含义完全依赖于 hash table 的用途和它所包含的数据。

## Properties

Properties 是 Hashtable 的一个子类。它用来包含值的列表，在这个列表中键是一个字符串并且值也是一个字符串。

Properties 类被很多其它 Java 类使用。例如，当获取环境变量值时，它是 System.getProperties( ) 这个方法返回值的对象类型。

