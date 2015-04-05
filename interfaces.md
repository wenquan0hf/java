# Java - 接口

接口是抽象方法的集合。如果一个类实现了一个接口，那么就需要继承这个接口中的所有抽象方法。

接口不是类。写一个接口和写一个类很相似，但是它们是两个不同的概念。类是描述一个对象的成员属性和行为。接口只包含一个类所实现的行为。

除非实现了接口的类是抽象的,否则接口中的所有方法都需要在类中实现。

在以下方面，接口和类非常相似：
- 一个接口可以包含任意数量的方法。
- 一个接口以 `.java` 的扩展名写入文件中，并且接口的名字与文件名相同。
- 接口的字节码位于一个 `.class` 文件中
- 接口位于包中，并且相应的字节码文件必须在和该包名匹配的文件夹结构下。

然而,在以下方面,接口和类是不同的:
- 不能实例化一个接口。
- 接口不能包含构造方法。
- 接口中的所有方法都是抽象的。
- 接口不能包含实例变量。接口中唯一能出现的变量必须被同时声明为 static 和 final 。
- 接口不能被类继承；它应该被类实现。
- 一个接口可以继承多个接口。

## 声明接口：

`interface` 关键字用来声明一个接口。下面是一个声明接口的简单例子：

### Example：

如下是描述了接口的例子：

```
/* File name : NameOfInterface.java */
import java.lang.*;
//Any number of import statements

public interface NameOfInterface
{
   //Any number of final, static fields
   //Any number of abstract method declarations\
}
```

接口有下述属性：
- 接口默认就是抽象的。当需要声明一个接口的时候不需要使用 `abstract` 关键字。
- 接口中的每个方法默认也是抽象的，所以 `abstract` 关键字也不需要。
- 接口中的方法默认是 public 的。

### Example：
```
/* File name : Animal.java */
interface Animal {

   public void eat();
   public void travel();
}
```

## 接口的实现：

当一个类实现一个接口的时候，你可以认为类就是签订一个条约，同意去执行接口中的各种行为。如果一个类没有实现接口中的所有行为，这个类就必须声明为 abstract 。

类使用 `implements` 关键字来实现一个接口。这个 `implements` 关键字写在类的声明部分中 extends（如果有） 部分的后面。

```
/* File name : MammalInt.java */
public class MammalInt implements Animal{

   public void eat(){
      System.out.println("Mammal eats");
   }

   public void travel(){
      System.out.println("Mammal travels");
   } 

   public int noOfLegs(){
      return 0;
   }

   public static void main(String args[]){
      MammalInt m = new MammalInt();
      m.eat();
      m.travel();
   }
} 
```

这将产生下面的结果：
```
Mammal eats
Mammal travels
```

当覆写定义在接口中的方法时，如下是需要遵守的几条规则：

- 异常不应该声明在实现的方法中，而是应该在声明的接口方法中或者那些声明方法的接口的子类。
- 当覆写方法的时候应该包含接口方法的签名和相同类型或子类型的返回值。
- 接口实现类本身可以是抽象的，如果是抽象的，则接口中的方法没必要全部实现。

当实现接口时有如下几条规则：
- 类可以一次性实现多个接口。
- 类只可以继承一个父类，但是可以实现多个接口。
- 一个接口可以继承自另一个接口，和一个类继承自另一个类的方法相同。

## 接口的继承

一个接口可以继承另一个接口，和一个类继承自另一个类的方法相同。 `extends` 关键字用来继承一个接口，并且子接口要继承父接口的所有方法。

下述的 Sports 接口 被 Hockey 和 Football 接口继承。
```
//Filename: Sports.java
public interface Sports
{
   public void setHomeTeam(String name);
   public void setVisitingTeam(String name);
}

//Filename: Football.java
public interface Football extends Sports
{
   public void homeTeamScored(int points);
   public void visitingTeamScored(int points);
   public void endOfQuarter(int quarter);
}

//Filename: Hockey.java
public interface Hockey extends Sports
{
   public void homeGoalScored();
   public void visitingGoalScored();
   public void endOfPeriod(int period);
   public void overtimePeriod(int ot);
}
```

Hockey 接口有四个方法，但是它从 Sports 接口中继承了两个；因此，一个实现了 Hockey 接口的类需要实现全部的六个方法。类似的，实现了 Football 的类需要定义 Football 接口中三个方法和 Sports 接口中的两个方法。

## 多个接口的继承：

一个 Java 类只可以继承一个父类，不可以多继承。 然而，接口不是类，一个接口可以继承多个父接口。


一旦使用了 `extends` 关键字，所有父接口声明时需要以逗号分隔。

例如，如果 Hockey 接口同时继承了 Sports 和 Event 接口，它需要像如下方式声明：
```
public interface Hockey extends Sports, Event
```

## 标记接口：
继承接口的最普通用法是父接口不包含任何的方法。例如， 在 java.awt.event 包中的 MouseListener 接口继承了 java.util.EventListener 接口，像如下定义：
```
package java.util;
public interface EventListener
{}
``` 

一个内部没有任何方法的接口被称为 `tagging` interface。 tagging interface 有两个基本的用途：

**创建一个共同的父类：** 像 EventListener 接口， 它继承了很多 Java API 中的其它接口，你可以使用 tagging interface 在一组接口中创建一个共同的父类。例如，当一个接口继承了 EventListener 接口的时候， Java 虚拟机（JVM）就知道这个特殊的接口被用在事件代理上。

**向类添加数据类型：** 一个实现了 tagging interface 的类是不需要定义任何方法的（因为这个接口中本来就没有任何方法），但是这个类通过多态的特性变成了一个接口类型。
