# Java 封装

封装是面向对象程序设计四大基本概念之一，其余三个分别是继承，多态和抽象。

封装是一种可以使类中的字段私有并能通过公有方法来访问私有字段的技术。如果一个字段被声明为私有，它就不能在类的外部被访问，从而隐藏了类内部的字段。基于这个原因，封装有时也被称为数据隐藏。

封装可以被认为是一种能够保护代码和数据被定义在类外的其它代码任意访问的屏障。访问数据和代码由一个接口严格控制。

封装的主要好处是修改我们实现的代码而又不会破坏其他人使用我们的代码。封装的这个特性使我们的代码具有可维护性、灵活性以及扩展性。

### 示例

如下是一个使用了封装的例子：

```
/* File name : EncapTest.java */
public class EncapTest{

   private String name;
   private String idNum;
   private int age;

   public int getAge(){
      return age;
   }

   public String getName(){
      return name;
   }

   public String getIdNum(){
      return idNum;
   }

   public void setAge( int newAge){
      age = newAge;
   }

   public void setName(String newName){
      name = newName;
   }

   public void setIdNum( String newId){
      idNum = newId;
   }
}
```

公有方法是从类外访问到类内字段的入口。通常情况下，这些方法被定义为 getters 和 setters 。因此想要访问类内变量的任何其他类要使用 getters 和 setters 方法。

EncapTest 类的变量可以像如下的方式访问：

```
/* File name : RunEncap.java */
public class RunEncap{

   public static void main(String args[]){
      EncapTest encap = new EncapTest();
      encap.setName("James");
      encap.setAge(20);
      encap.setIdNum("12343ms");

      System.out.print("Name : " + encap.getName()+ 
                             " Age : "+ encap.getAge());
    }
}
```

这将产生下述结果：

```
Name : James Age : 20
```

## 封装的优点

- 类中的字段可以被设置为只读或只写。
- 类可以完全控制它字段里面所存储的东西。
- 类的使用者不用知道类是如何存储数据的。类可以改变字段的数据类型而类的使用者不需要改变任何之前的代码。