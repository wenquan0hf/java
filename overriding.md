# Java 重写

在上一章节中，我们讨论了父类和子类。如果一个类从它的父类继承了一个方法，如果这个方法没有被标记为 final ，就可以对这个方法进行重写。

重写的好处是：能够定义特定于子类类型的行为，这意味着子类能够基于要求来实现父类的方法。

在面向对象编程中， overriding 意味着去重写已经存在的方法。

### 示例

让我们来看以下的例子：

```
class Animal{

   public void move(){
      System.out.println("Animals can move");
   }
}

class Dog extends Animal{

   public void move(){
      System.out.println("Dogs can walk and run");
   }
}

public class TestDog{

   public static void main(String args[]){
      Animal a = new Animal(); // Animal reference and object
      Animal b = new Dog(); // Animal reference but Dog object

      a.move();// runs the method in Animal class

      b.move();//Runs the method in Dog class
   }
}
```

这将产生如下结果：

```
Animals can move
Dogs can walk and run
```

在上面的例子中，你可以看到尽管 b 是 Animal 类型，但它运行了 dog 类的方法。原因是：在编译时会检查引用类型。然而，在运行时，JVM 会判定对象类型到底属于哪一个对象。

因此，在上面的例子中，虽然 Animal 有 move 方法，程序会正常编译。在运行时，会运行特定对象的方法。

考虑下面的例子：

```
class Animal{

   public void move(){
      System.out.println("Animals can move");
   }
}

class Dog extends Animal{

   public void move(){
      System.out.println("Dogs can walk and run");
   }
   public void bark(){
      System.out.println("Dogs can bark");
   }
}

public class TestDog{

   public static void main(String args[]){
      Animal a = new Animal(); // Animal reference and object
      Animal b = new Dog(); // Animal reference but Dog object

      a.move();// runs the method in Animal class
      b.move();//Runs the method in Dog class
      b.bark();
   }
}
```


这将产生如下结果：

```
TestDog.java:30: cannot find symbol
symbol  : method bark()
location: class Animal
                b.bark();
                 ^
```

这个程序在编译时将抛出一个错误，因为 b 的引用类型 Animal 没有一个名字叫 bark 的方法。

## 方法重写规则

- 重写方法的参数列表应该与原方法完全相同。
- 返回值类型应该和原方法的返回值类型一样或者是它在父类定义时的子类型。
- 重写函数访问级别限制不能比原函数高。举个例子：如果父类方法声明为公有的，那么子类中的重写方法不能是私有的或是保护的。
- 只有被子类继承时，方法才能被重写。
- 方法定义为 final，将导致不能被重写。
- 一个方法被定义为 static，将使其不能被重写，但是可以重新声明。
- 一个方法不能被继承，那么也不能被重写。
- 和父类在一个包中的子类能够重写任何没有被声明为 private 和 final 的父类方法。
- 和父类不在同一个包中的子类只能重写 non-final 方法或被声明为 public 或 protected 的方法。
- 一个重写方法能够抛出任何运行时异常，不管被重写方法是否抛出异常。然而重写方法不应该抛出比被重写方法声明的更新更广泛的已检查异常。重写方法能够抛出比被重写方法更窄或更少的异常。
- 构造函数不能重写。

## 使用 super 关键字

当调用父类的被重写的方法时，要用关键字 super。

```
class Animal{

   public void move(){
      System.out.println("Animals can move");
   }
}

class Dog extends Animal{

   public void move(){
      super.move(); // invokes the super class method
      System.out.println("Dogs can walk and run");
   }
}

public class TestDog{

   public static void main(String args[]){

      Animal b = new Dog(); // Animal reference but Dog object
      b.move(); //Runs the method in Dog class

   }
}
```

这将产生如下结果:

```
Animals can move
Dogs can walk and run
```
