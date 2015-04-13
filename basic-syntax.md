# Java 基本语法  

Java 应用程序可以被定义为对象的集合，这些对象通过调用各自的方法来进行通信。下面让我们具体看一看类，对象，方法，实体变量是什么含义。  
- **对象:**对象具有状态和行为。例如：狗有它的状态—颜色，名字，品种，同时也有行为—摇尾巴，汪汪叫，吃东西。对象时类的一个实例。  
- **类:**类可以被定义为描述对象所支持的类型的行为和状态的模板或蓝图。  
- **方法:**方法是一种基本的行为。类中可以包含很多方法。在方法中，可以编写逻辑，操纵数据，执行动作。  
- **实体变量:**每个对象都有它的特殊的实体变量的集合，一个对象的状态是由那些实体变量所被赋的值所决定的。  

## 第一个 Java 程序：  
让我们看一下下面可以输出 “Hello World” 的代码。
```
public class MyFirstJavaProgram {

   /* This is my first java program.  
    * This will print 'Hello World' as the output
    */

    public static void main(String []args) {
       System.out.println("Hello World"); // prints Hello World
    }
} 
```  

让我们看一下如何保存这个文件，编译运行这个程序。请按照以下步骤操作：  
- 打开记事本添加上述代码  
- 以 MyFirstJavaProgram.java 为文件名保存文件  
- 打开命令提示符窗口转到你保存类的位置。假设是 C:\  
- 在窗口中输入 javac MyFirstJavaProgram.java 然后按回车来编译你的代码。如果你的代码没有错误，那么命令提示符将会转到下一行（假设：路径变量设置成功）。  
- 现在输入 java MyFirstJavaProgram 来运行你的程序  
- 你将会看到屏幕上显示 “Hello World”  
```
C : > javac MyFirstJavaProgram.java
C : > java MyFirstJavaProgram
Hello World
```

## 基本语法：  
关于 Java 程序，记住一下几点很重要。  
- **大小写敏感性**： Java 是一种大小写敏感的语言，这就意味着 **Hello** 和 **hello** 在 Java 中代表不同的意思。  
- **类的名称**：所有类的名称首字母必须大写。  
如果类名称中包含几个单词，那么每个单词的首字母都要大写。  
例如类 MyFirstJavaClass  
- **方法名称**：所有方法名称必须以小写字母开头。  
如果方法名称中包含几个单词，那么其中的每个单词的首字母都要大写。  
例如 public void myMethodName()  
- **程序文件名**：程序的文件名必须和类的名称准确匹配。  
但保存文件时，你应当以类的名称保存（注意区分大小写），并在文件名后加 .java 的后缀（如果文件名和类名不匹配那么将无法编译你的程序）。  
例如：假设类名是 MyFirstJavaProgram，那么文件名就应该是 MyFirstJavaProgram.java。  
- **Java 程序的入口地址**：Java 程序都是从 main（） 方法开始处理的，这个方法是 Java 程序的强制性的部分。  

## Java 标识符  
Java 的所有的组成部分都要有自己的名称。类、变量和方法的名称称为标识符。  
在 Java 中，需要记住关于标识符的一下几点。如下：  
- 所有标识符必须以字母（ A 到 Z 或者 a 到 z ）、货币字符（ $ ）或者下划线( _ )开头。  
- 在第一个标识符之后可以有任意字母组合。  
- 关键字不能被用作标识符。  
- 大多数标识符需要区分大小写。  
- 合法标识符的例子： age, $salary, _value, __1_value  
- 非法标识符的例子： 123abc, -salary  

## Java 修饰符  
如其语言一样，方法和类等等是可以通过修饰符修饰的。Java 中有两种修饰符：  
- **访问修饰符**：default, public , protected, private  
- **非访问修饰符**：final, abstract, strictfp  
我们将在下一节继续学习修饰符相关知识。  

## Java 变量  
在 Java 中我们可以看到如下变量：  
- 本地变量  
- 类变量（静态变量）  
- 实例变量（非静态变量）  

## Java 数组  
数组时储存有多重相同变量类型的对象。然而，数字自身也是堆中的一个对象。我们将要学习如何声明，建立，初始化数组。  

## Java 枚举值  
枚举是在 Java5.0 版本中被引进的。枚举限制了变量要有一些预先定义的值。枚举列表中的值称为枚举值。  
运用枚举值可以大大减少你的代码中的漏洞。  
举例来说，如果我们想为一家鲜榨果汁店编个程序，就可以将杯子的尺寸限制为小中和大。这样就可以确保人们不会定大中小尺寸之外的了。  
例如：  
```
class FreshJuice {

   enum FreshJuiceSize{ SMALL, MEDIUM, LARGE }
   FreshJuiceSize size;
}

public class FreshJuiceTest {

   public static void main(String args[]){
      FreshJuice juice = new FreshJuice();
      juice.size = FreshJuice. FreshJuiceSize.MEDIUM ;
      System.out.println("Size: " + juice.size);
   }
}
```  

上述例子会输出如下结果：  
```
Size: MEDIUM
```  

**注**：枚举可以自己声明也可以在类中声明。方法变量和构造器也可以在枚举值中定义。      

## Java 关键字    
下面列出的是 Java 中保留的单词。这些单词不能用作常量、变量和其他标识符的名字。 
abstract assert boolean break byte case catch char class const continue default do double else enum extends final finally float for goto if implements import instanceof int interface long native new	package private	protected public return short static strictfp super switch synchronized this throw throws transient try void volatile while  	 

## Java 中的注释    
Java 像 C 和 C++ 一样支持单行或多行注释。所有注释中的字母都会被 Java 编译器忽略。    
```
public class MyFirstJavaProgram{

   /* This is my first java program.
    * This will print 'Hello World' as the output
    * This is an example of multi-line comments.
    */

    public static void main(String []args){
       // This is an example of single line comment
       /* This is also an example of single line comment. */
       System.out.println("Hello World"); 
    }
} 
```
## 使用空行：  
一行只有空格的行可能是注释，这样的行叫做空行，Java会完全忽略它。  
  
## 继承：  
在 Java 中类可以从类中产生。简单来说，如果你想要创建一个新类并且现在已经存在一个包含你所需要代码的类，那么就有可能从这些存在的代码创建你的类。  
这个概念可以使你在没有在新类中重写代码的情况下重复利用文件和方法。在这种情况下已经存在的类叫做超类，后来产生的类叫做子类。  

## 接口：    
在 Java 语言中，接口可以定义为对象之间如何通信的合同。就继承性而言接口扮演了重要角色。  
接口定义了子类所需要用的方法。但是方法的实施还是取决于子类。  

## 接下来是什么呢？  
下一节将讲解Java编程中的对象和类。在该章节末你就会清楚了解什么是Java中的对象和类。  
