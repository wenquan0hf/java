# Java 继承

继承可以被定义为一个对象获取另一个对象属性的过程。使用继承可以使信息以继承顺序有序管理。

当我们谈论起继承，最常用的关键字应该为 extends 和 implements。
这些关键字将决定一个对象是否是 A 类型或是其他类型。通过使用这些关键字,我们可以使一个对象获得另一个对象的属性。

## IS-A 关系

IS-A 是说：这个对象所属于另一个对象。让我们来看怎么用关键字 extends 来实现继承。

```
public class Animal{
}

public class Mammal extends Animal{
}

public class Reptile extends Animal{
}

public class Dog extends Mammal{
}
```

现在,基于上面的例子,在面向对象编程中,请遵循以下几点:
- Animal 是 Mammal 类的父类。
- Animal 是 Reptile 类的父类。
- Reptile 和 Mammal 是 Animal 类的子类。
- Dog 是 Mammal 类和 Animal 类的子类。

现在，针对 IS-A 关系，我们可以说:
- Mammal 是一个 Animal
- Reptile 是一个 Animal
- Dog 是一个 Mammal
- Dog 也是一个 Animal

使用关键字 extends，子类可以继承父类除了私有属性的所有属性。

使用 instance 操作我们可以保证 Mammal 实际上是一个 Animal。

### 示例

```
public class Dog extends Mammal{

   public static void main(String args[]){

      Animal a = new Animal();
      Mammal m = new Mammal();
      Dog d = new Dog();

      System.out.println(m instanceof Animal);
      System.out.println(d instanceof Mammal);
      System.out.println(d instanceof Animal);
   }
}
``` 

这将得到如下结果：

```
true
true
true
```

我们已经很好理解了 extends 关键字，让我们来看 implements 关键字是如何确立 IS-A 关系的。

implements 关键字，是在类继承接口的时候使用的。接口是不能被类使用 extends 继承的。

### 示例

```
public interface Animal {}

public class Mammal implements Animal{
}

public class Dog extends Mammal{
}
```

## 关键字 instanceof

让我们使用 instanceof 操作符来检查确定是否 Mammal 实际上是 Animal, dog 实际上是一种Animal。

```
interface Animal{}

class Mammal implements Animal{}

public class Dog extends Mammal{
   public static void main(String args[]){

      Mammal m = new Mammal();
      Dog d = new Dog();

      System.out.println(m instanceof Animal);
      System.out.println(d instanceof Mammal);
      System.out.println(d instanceof Animal);
   }
} 
```

这将产生如下结果：

```
true
true
true
```

## HAS-A 关系：

该关系是基于使用方便的。这决定了一个类是否含有 A 的一些属性。该关系帮助减少代码重复和漏洞的出现。

让我们看下面的例子:

```
public class Vehicle{}
public class Speed{}
public class Van extends Vehicle{
	private Speed sp;
} 
```

这个例子表明 Van 含有 Speed.因为我们单独定义了 Speed 类，我们不必将整个 Speed 类的代码加入 Van 类，使其在多个应用程序中重用 Speed 类。


在面向对象中，用户不用去考虑哪一个对象在做实际的工作。为了实现这个功能， Van 类向用户隐藏了实现具体细节的类。当用户让 Van 类去做一项工作时，Van 类或者自己来做，或者求助其他类来做这项工作。

请记住一个非常重要的事实，Java 只支持单继承，这意味着一个类只能继承一个类，所以以下的是非法的：

```
public class extends Animal, Mammal{} 
```

然而，一个类可以实现一个或多个接口，这使得 Java 可以摆脱不能多继承的问题。