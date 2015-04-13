# Java - 多态性

多态性是指对象能够有多种形态。在 OOP 中最常用的多态性发生在当父类引用指向孩子类对象时。

任何能够通过一个以上的 IS-A 测试的 Java 对象被认为是多态的。在Java中所有对象都是多态的，因为任何一个对象都会有一个他们自己类型的和Object类的 IS-A 测试。


重要的是知道，通过引用变量是唯一可以用来访问一个对象的方法。引用变量可以只有一个类型。引用变量一旦被声明是不能被改变的。

引用变量能够重新分配到其他提供的没有被声明为 final 的对象。引用变量的类型将决定他可以调用的对象的方法。

一个引用变量能够引用任何一个对象的声明类型或任何声明类型的子类型。一个引用变量可以声明为一个类或接口类型。

## 例子：
让我们看下面的例子：

```
public interface Vegetarian{}
public class Animal{}
public class Deer extends Animal implements Vegetarian{}
```

现在 Deer 类是多态的，因为他有多个继承机制。针对上面的例子有以下说法：

- Deer 就是 Animal
- Deer 就是 Vegetarian
- Deer 就是 Deer
- Deer 就是 Object

当我们提供引用变量来引用 Deer 对象，下面的声明是合法的：

```
Deer d = new Deer();
Animal a = d;
Vegetarian v = d;
Object o = d;
```

所有的引用变量 d,a,v,o 在堆中引用同一个对象 Deer。

## 虚方法

在这一节中，我将向您展示在 Java 中被覆盖方法的行为在你设计类时是如何体现多态性的好处的。

我们已经讨论了覆盖方法，一个子类可以覆盖他父类的方法。一个被覆盖的方法实际上隐藏在父类当中，并且不会被调用，除非子类在覆盖方法中用 super 关键字。

```
/* File name : Employee.java */
public class Employee
{
   private String name;
   private String address;
   private int number;
   public Employee(String name, String address, int number)
   {
      System.out.println("Constructing an Employee");
      this.name = name;
      this.address = address;
      this.number = number;
   }
   public void mailCheck()
   {
      System.out.println("Mailing a check to " + this.name
       + " " + this.address);
   }
   public String toString()
   {
      return name + " " + address + " " + number;
   }
   public String getName()
   {
      return name;
   }
   public String getAddress()
   {
      return address;
   }
   public void setAddress(String newAddress)
   {
      address = newAddress;
   }
   public int getNumber()
   {
     return number;
   }
}
```

现在我们如下继承 Employee 类：

```
/* File name : Salary.java */
public class Salary extends Employee
{
   private double salary; //Annual salary
   public Salary(String name, String address, int number, double
      salary)
   {
       super(name, address, number);
       setSalary(salary);
   }
   public void mailCheck()
   {
       System.out.println("Within mailCheck of Salary class ");
       System.out.println("Mailing check to " + getName()
       + " with salary " + salary);
   }
   public double getSalary()
   {
       return salary;
   }
   public void setSalary(double newSalary)
   {
       if(newSalary >= 0.0)
       {
          salary = newSalary;
       }
   }
   public double computePay()
   {
      System.out.println("Computing salary pay for " + getName());
      return salary/52;
   }
}
```

现在,你仔细研究下面的程序,试图确定它的输出:

```
/* File name : VirtualDemo.java */
public class VirtualDemo
{
   public static void main(String [] args)
   {
      Salary s = new Salary("Mohd Mohtashim", "Ambehta, UP", 3, 3600.00);
      Employee e = new Salary("John Adams", "Boston, MA", 2, 2400.00);
      System.out.println("Call mailCheck using Salary reference --");
      s.mailCheck();
      System.out.println("\n Call mailCheck using Employee reference--");
      e.mailCheck();
    }
}
```

这将产生如下的结果:

```
Constructing an Employee
Constructing an Employee
Call mailCheck using Salary reference --
Within mailCheck of Salary class
Mailing check to Mohd Mohtashim with salary 3600.0

Call mailCheck using Employee reference--
Within mailCheck of Salary class
Mailing check to John Adams with salary 2400.0
```

这里我们实例化两个 Salary 对象。一个用 Salary 引用 s，另一个用Employee引用 e。

当调用 s.mailCheck() 方法时，编译器在编译时发现 mailCheck() 在 Salary类中，并且 JVM 在运行时调用 Salary类的 mailCheck() 方法。

调用 e 的 mailCheck() 是略有不同的因为 e 是一个 Employee的引用。当编译器发现 e.mailCheck() 时,编译器在 Employee 类中发现 mail.Check() 方法。

这里,在编译时,编译器使用 Employee 的 mailCheck() 方法来验证。在运行时，JVM 调用 Salary 类的 mailCheck() 类。

这种行为被称为虚方法调用，该方法也被称为虚方法。Java 中所有此规则的方法行为，无论是什么数据类型的引用，运行时会调用被覆盖方法，在编译时都会遵循于源码。
