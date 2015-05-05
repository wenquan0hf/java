# Java 包

在 Java 中使用包是为了防止命名冲突，来控制访问，使得搜索/定位和类、接口、枚举和注释等的使用更为简单。

包可以被定义为一组相关的类型（类、接口、枚举和注释），提供访问保护和命名空间管理。

在 Java 中一些已经存在的包有：
- `java.lang` - 包含了基本类
- `java.io` - 包含有输入，输出功能的类

程序员可以定义自己的包来包含各种类和接口等。把你实现的相关类组织在一起是一种很好的做法，这样一个程序员可以很简单的知道哪些类、接口、枚举，注释是相关的。

由于包创建了一个新的命名空间，因此将不会和其他包中的名字有任何名字冲突。使用包，可以很简单的提供访问控制，并且也可以很简单的定位到相关类。

## 创建包

当创建一个包的时候，应该为包起一个名字，并且把 `package` 名字的声明语句放在每个包含类、接口、枚举和注释类型的源文件顶部。

`package` 声明语句应该放在源文件的第一行。在每个源文件中只能有一个包声明语句，并且它适用于所有类型的文件。

如果没有使用包声明，那么类、接口、枚举和注释类型的将会被放进一个无名的包中。

### 示例

让我们来看创建了一个叫做 `Animal` 的包的例子。习惯上使用小写名字的包以避免和类、接口名字的冲突。

在包 *animals* 中声明一个接口：

```
/* File name : Animal.java */
package animals;

interface Animal {
   public void eat();
   public void travel();
}
```

现在，在同一个包 *animals* 中实现一个类：

```
package animals;

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

现在，你可以编译这两个文件并将它们放置在一个叫做 `animals` 的子文件夹中，然后像下述来运行：

```
$ mkdir animals
$ cp Animal.class  MammalInt.class animals
$ java animals/MammalInt
Mammal eats
Mammal travels
```

## import 关键字

如果一个类想使用同一个包中的另一个类，就没必要使用包名。同一个包中的类不用任何特殊的语法就可以彼此识别。

### 示例

一个叫做 Boss 的类添加进了已经包含了 Employee 的 payroll 包中。 在没有使用 payroll 前缀的情况下，Boss 类引用了 Employee 类，像下面演示的 Boss 类：

```
package payroll;

public class Boss
{
   public void payEmployee(Employee e)
   {
      e.mailCheck();
   }
}
```

如果 Boss 类 没有在 payroll 包中会发生什么？那么 Boss 类就必须使用下述的其中一种方法来引用位于其它包中的类。
- 可以使用全名。例如：

```
payroll.Employee
```

- 可以使用 import 关键字和通配符（*）来导入。例如：

```
import payroll.*;
```

- 可以使用 import 关键字来导入类本身。例如：

```
import payroll.Employee;
```

**注：** 一个类的文件可以包含任意数量的导入语句。这些导入语句必须位于包声明语句之后和类的定义语句之前。

## 包的目录结构

当一个类放置在一个包中时主要会发生以下两个结果：
- 包的名字变成了类名字的一部分，就像我们在前一个章节刚刚讨论过的。
- 包的名字必须和相关字节码文件的目录结构匹配。

在 Java 里有以下一种管理文件的简单方式：

将类、接口、枚举、注释类型的源代码存在一个扩展名为 `.java` 的文本文件中。例如：

```
// File Name :  Car.java

package vehicle;

public class Car {
   // Class implementation.   
}
```

现在，将源文件放在一个其名字能够反映出包的名字的文件夹中：

```
....\vehicle\Car.java
```

现在，正确的类名和路径名应该像下面这样：
- 类名 -> vehicle.Car
- 路径名 -> vehicle\Car.java (in windows)

一般情况下，一个公司使用它的逆序的互联网域名当做包的名称。例如：某公司的互联网域名是 apple.com ，那么它的包名应该是以 com.apple 开头。包名的每一个部分反映了一个子目录。

例如：一个公司有一个包含了 Dell.java 源文件的 com.apple.computers 的包，它将被包含在像下面的一系列子文件夹中：

```
....\com\apple\computers\Dell.java
```

在编译的时候，编译器为其中定义的每个类、接口和枚举创建了一个不同的输出文件。输出文件的基本名字是类型名和 `.class` 的扩展名。

例如:

```
// File Name: Dell.java

package com.apple.computers;
public class Dell{
      
}
class Ups{
      
}
```

现在，像下面使用 -d 选项来编译这个文件：

```
$javac -d . Dell.java
```

这将像下面存放编译后的文件：

```
.\com\apple\computers\Dell.class
.\com\apple\computers\Ups.class
```

你可以像下面这样导入所有定义在 *\com\apple\computers\* 中的类和接口：

```
import com.apple.computers.*;
```

像 .java 这样的源文件， .class 这些编译后的文件应该在能够反映出包名的一系列文件夹中。然而， .class 文件的路径不用和 .java 源文件的路径相同。你可以独立的管理源文件和编译后文件的目录，如下：

```
<path-one>\sources\com\apple\computers\Dell.java

<path-two>\classes\com\apple\computers\Dell.class
```

通过这样，可以把编译过后的文件夹给其它的程序员而不用暴露你的源文件。同时你也需要使用这种方式来管理源文件和编译过后的 class 文件以便编译器和 Java 虚拟机（JVM）能够找到程序中使用的所有类型。

编译后文件夹的全路径， \<path-two>\classes， 叫做 class path， 在系统环境变量 CLASSPATH 中设置。编译器和 JVM 通过添加包名到 class path 中来构造 .class 文件的路径。

我们说 \<path-two>\classes 是 class path， 包名是 com.apple.computers ，然后编译器和 JVM 将在 \<path-two>\classes\com\apple\compters 中寻找 .class 文件。

一个 class path 可能包含几个路径。多个路径以分号（Windows）或者冒号（Unix）隔开。默认情况下，编译器和 JVM 查找当前目录和包含 Java 平台字节码的 JAR 文件以便于这些文件夹自动在 class path 中。

## 设置系统中的 CLASSPATH 环境变量

为了显示当前的 CLASSPATH 环境变量，使用以下在 Windows 和 UNIX（Bourne shell）中的命令：
- 在 Windows 中 -> C:\> set CLASSPATH
- 在 UNIX 中 -> % echo $CLASSPATH

使用下述命令删除当前 CLASSPATH 变量中的内容：
- 在 Windows 中 -> C:\> set CLASSPATH=
- 在 UNIX 中 -> % unset CLASSPATH; export CLASSPATH

使用下述命令设置 CLASSPATH 变量：
- 在 Windows 中 -> set CLASSPATH=C:\users\jack\java\classes
- 在 UNIX 中 -> % CLASSPATH=/home/jack/java/classes; export CLASSPATH