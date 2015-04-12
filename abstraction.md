#Java - 抽象

Abstraction 是指在 OOP 中 让一个类抽象的能力。一个抽象类是不能被实例化的。类的功能仍然存在，他的字段，方法和构造函数都以相同的方式进行访问。你只是不能创建一个抽象类的实例。

如果一个类是抽象的，即不能被实例化，这个类若果不是子类他将没有什么作用。这体现了在设计过程中抽象类是如何被提出的。一个父类包含子类的基本功能集合，但是父类是抽象的，不能自己去使用功能。

##抽象类

使用关键字 abstract 来声明一个抽象类。它出现在关键字 class 的前面。

```
/* File name : Employee.java */
public abstract class Employee
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
   public double computePay()
   {
     System.out.println("Inside Employee computePay");
     return 0.0;
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

注意, Employee 类没什么不同。类现在是抽象的,但它仍然有三个字段,七个方法,一个构造函数。

现在如果你尝试一下代码：

```
/* File name : AbstractDemo.java */
public class AbstractDemo
{
   public static void main(String [] args)
   {
      /* Following is not allowed and would raise error */
      Employee e = new Employee("George W.", "Houston, TX", 43);

      System.out.println("\n Call mailCheck using Employee reference--");
      e.mailCheck();
    }
}
```

当你进行编译时，你将得到下面的错误：

```
Employee.java:46: Employee is abstract; cannot be instantiated
      Employee e = new Employee("George W.", "Houston, TX", 43);
                   ^
1 error
```

##继承抽象类:

我们可以如下继承 Employee 类：

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

这里，我们不能实例化一个新的 Employee，但是如果我们实例化一个新的 Salary 对象，Salary 对象将继承 Employee 的三个字段和七个方法。

```
/* File name : AbstractDemo.java */
public class AbstractDemo
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
这将产生如下结果：

```
Constructing an Employee
Constructing an Employee
Call mailCheck using  Salary reference --
Within mailCheck of Salary class
Mailing check to Mohd Mohtashim with salary 3600.0

Call mailCheck using Employee reference--
Within mailCheck of Salary class
Mailing check to John Adams with salary 2400.
```

##抽象方法

如果你想一个提供特定方法的类，但是你想要在他的子类中实际实现这个方法，你可以在父类中声明这个方法为抽象的。

abstract 关键字也被用来定义抽象方法。一个抽象方法是有方法签名的但没有方法实体。

抽象方法无需定义，并且它的签名以分号结束，不需要花括号。

```
public abstract class Employee
{
   private String name;
   private String address;
   private int number;
   
   public abstract double computePay();
   
   //Remainder of class definition
}
```
声明一个抽象方法有两个结果:

- 如果一个类中含有一个抽象方法，类必须也是抽象的。
- 任何一个子类必须覆盖这个抽象方法，或者继续将它声明为抽象方法。

子类继承一个抽象方法，必须要去覆盖他。如果不这样做的话，他们必须将其继续声明为抽象，或在他们的子类中去覆盖他。

最终，后代类不得不去实现抽象方法；否则你能一直有一个不能被实例化的抽象类。

如果 Salary 继承 Employee 类，则他必须如下要去实现computerPay()方法：

```
/* File name : Salary.java */
public class Salary extends Employee
{
   private double salary; // Annual salary
  
   public double computePay()
   {
      System.out.println("Computing salary pay for " + getName());
      return salary/52;
   }

   //Remainder of class definition
}
```
