# Java-快速参考指南
## 什么是 Java?
- 面向对象  

- 平台独立  

- 简单  

- 安全  

- 中立  

- 可移植的  

- 强健  

- 多线程  

- 可翻译的  

- 高效  

- 分布式的  

- 动态的

## Java 基本语法：  
- **Object**-对象有状态和行为。例子：一条狗有状态：颜色，名字，品种以及行为-摇尾巴，吠，吃。一个对象是一个类的实例。  
- **Class**-一个类能被定义成一个描述行为/状态的它所在类型的对象支持的模板/蓝图。  
- **Methods**-一个方法基本是一个行为。一个类能包含许多方法。逻辑是写在方法中的，数据被操作并且所有的行为被执行。  
- **即时变量**-每一个对象有它独有即时变量的设置。一个对象的状态由赋予这些即时变量的值所创建。  

## 第一个 Java 程序：
让我们看看一个简单的能打印出单词 Hello World 的代码。
```
public class MyFirstJavaProgram{

   /* This is my first java program.  
    * This will print 'Hello World' as the output
    */

    public static void main(String []args){
       System.out.println("Hello World"); // prints Hello World
    }
} 
```
关于 Java 程序，记住下面几点很重要。  

- **大小写敏感性**-Java 是区分大小写，这意味着标识符 Hello 和 hello 在 Java 中将有不同的含义。  
- **类名**-对于所有的类名来说第一个字母应该是大写的。  
如果几个单词被用来组成类的名字则每一个内部的单词的第一个应该是大写的。  
例子： 类 MyFirstJavaClass  
- **方法名字**-所有的方法名英爱以一个小写字母开始。  
如果几个单词背用来组成方法的名字，则每个内部单词的第一个字母应该是大写的。  
例子：public void myMethodName()  
- **程序文件名**-程序文件的名字应该准确匹配类名。  
当保存文件时你应该使用类名(记住 java 是大小写区分的)并且在文件名字末尾附加".java"。(如果文件名和类名不匹配，你的程序将不会编译)  
例子：假设'MyFirstJavaProgram'是类名，那么文件应该被保存为'MyFirstJavaProgram.java'。  
- **public static void main(String args[])**-java 程序处理从 main()方法开始，这是每个 java 程序的强制部分。  

## Java 标识符：
所有的 Java 成分需要名字。类，变量和方法的名字呗叫做标识符。  

在 java 中有关标识符有几点需要记住。它们是以下几点：
- 所有的标识符应该以字母(A 到 Z或者 a 到 z)，货币符号($)或者一个下划线(_)。
- 在第一个字符后，标识符可以有任意字符的组合。  
- 关键词不能被用作标识符。
- 最重要的是标识符是区分大小写的。
- 合法标识符的例子:age,$salary,_value,_1_value
- 非法标识符的例子:123abc,-salary  

## Java 修饰符：
像其他语言，使用修饰符修改类，方法等等是有可能的。有两种修饰符。  
- **访问修饰符:**default,public,protected,private
- **非访问修饰符:**final,abstract,strictfp  
我们将在下一节寻找更多有关修饰符的细节。  

## Java 变量:
我们将看到在 java 中变量的以下类型：
- 本地变量
- 类变量(静态变量)
- 实例变量(非静态变量)  

## Java 数组:
数组是存储同一类型多个变量的对象。然而一个数组自身是堆上的一个对象。我们将在下一章调查如何声明，构建和初始化。  

## Java 枚举:
枚举是在 Java 5.0 中被引进的。枚举限制了一个变量拥有几个预先定义的值中的一个。在枚举列表中的值被称为枚举。  

使用枚举减少你代码中的 bug 是有可能的。  

例如如果我们为一个新鲜果汁商店考虑一个应用程序，限制杯子的形状小，中，大是有可能的。这将确保没有任何人可以点出了小，中，大之外的型号。  

## 例子：
```
class FreshJuice{

   enum FreshJuiceSize{ SMALL, MEDIUM, LARGE }
   FreshJuiceSize size;
}

public class FreshJuiceTest{

   public static void main(String args[]){
      FreshJuice juice = new FreshJuice();
      juice.size = FreshJuice. FreshJuiceSize.MEDIUM ;
      System.out.println("Size :" + juice.size);
   }
}
```
**注意：**枚举能被自身声明或者在一个类中。方法，变量，构造函数也能在枚举中被定义。  

## Java 关键词：
以下的列表展示了 java 中的保留字。这些保留字可能不会被作为常量或者变量或者任何其他标识符的名字而使用。  

|||||
|----------|:----------:|-----:|
|abstract|assert|boolean|break|
|byte|case|catch|char|
|class|const|continue|default|
|do|double|else|enum|
|extends|final|finally|float|
|for|goto|if|implements|
|import|instanceof|int|interface|
|long|native|new|package|
|private|protected|public|return|
|short|static|strictfp|super|
|switch|synchronized|this|throw|
|throws|transient|try|void|
|volatile|while|||


## Java 中的注释
Java 像 C 和 C++ 一样支持单行和多行注释。所有的在注释中的可获得的字符都会被 java 编译器忽略。  
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
## Java 中的数据类型
在 java 中有两种数据类型:  
- 原始数据类型  
- 引用/对象数据类型  

## 原始数据类型:  
Java 支持的总共有 8 种原始数据类型。原始数据类型是由语言预定义的并且由关键字命名。让我们现在仔细看看有关 8 种原始数据类型的细节。  
- byte  
- short  
- int  
- long  
- float  
- double  
- boolean  
- char  

## 引用数据类型 
- 引用变量是使用定义的类的构造函数创建的。它们被用来访问对象。这些变量被声明为一个特定的不能改变的类型。举例来说，Employee,Puppy 等等。  
- Class 类，和不同的数组变量类型归入引用数据类型。  
- 任何引用变量的默认值是 null。  
- 一个引用变量能被用来指向任何声明类型的对象或者任何兼容的类型。  
- 例子:Animal animal = new Animal("giraffe");  

## Java 字面量
一个字面量是由固定值表示的源代码。它们用代码直接表示而没有任何计算。  

字面值可以被赋给任何原始数据类型。例如:  
```
byte a = 68;
char a = 'A'
```
Java 中的  String 字面值是指定的，就像它们在大部分其他的语言中通过在一对双引号间包含一系列的字符。String 字面值的例子如下：  

|记号      |符号表示   |
|----------|:----------:|-----:|
|\n|新的一行(0x0a)|
|\r|回车(0x0d)|
|\f|进纸(0x0c)|
|\b|退格(0x08)|
|\s|空格(0x20)|
|\t|制表符|
|\"|双引号|
|\'|点引号|
|\\|反斜线|
|\ddd|八进制字符|
|\uxxxx|十六进制 UNICODE 字符|
```
"Hello World"
"two\nlines"
"\"This is in quotes\""
```
Java 语言给 String 和 char 字面值支持很少的特殊的换码序列。它们是:  

## Java 访问修饰符:  
Java 提供许多访问修饰符来为类，变量，方法和构造函数设置访问等级。四个访问等级如下:  
- 对包可见。默认。不需要修饰符。
- 仅对类(private)可见
- 对世界可见(public)
- 对包和所有的子类可见(protect)  

## Java 基本运算符号:  
Java 给操作变量提供了一组丰富的操作符。我们可以将所有的 Java 操作符区分成以下几组:  

## 算数操作符:

|运算符     |描述   |例子|
|----------|:----------:|-----:|
|+|加-在操作符的每一侧加值|A + B 将得出30|
|-|减-从左边的操作数中减去右边的操作数|A - B 将得出 -10|
|*|乘-在操作符的每一侧倍增值|A \* B 将得出 200|
|/|除-用右边的操作数除左边的操作数|B \ A 将得出2|
|%|模-用右边的操作数除左边的操作数并返回余数|B % A 将得出0|
|++|增值-操作数的值增加 1|B++ 得出21|
|--|减量-操作数的值减少 1|B-- 得出19|

## 关系操作符:

|运算符     |描述   |例子|
|----------|:----------:|-----:|
|==|查看两个操作数的值是否相等，如果是的话，情况就是真。|(A == B)不为真|
|!=|查看两个操作数的值是否相等，如果值不相等，情况就是真。|(A != B)为真|
|>|查看左边操作数的值是否大于右边的操作数，如果是的话，情况就是真。|(A > B)不为真|
|<|查看左边操作数的值是否小于右边的操作数，如果是的话，情况就是真。|(A < B)为真|
|>=|查看左边操作数的值是否大于或等于右边的操作数，如果是的话，情况就是真。|(A >= B)不为true.|
|<=|查看左边操作数的值是否小于或等于右边的操作数，如果是的话，情况就是真。|(A <= B)为true.|

## 按位操作符:  

|运算符     |描述   |例子|
|----------|:----------:|-----:|
|&|二进制的与操作符将一个位复制到结果中如果它存在于两个操作数中|(A & B)将得出 12 即 0000 1100|
|\||二进制的或操作符复制一个位如果它存在在两个操作数中的一个|(A \| B)将得出 61 即 0011 1101|
|^|二进制的异或操作符复制一个位如果它在一个而不是两个操作数中被设置。|(A ^ B)将得出 49 即 0011 0001|
|~|二进制补运算符是一元的，并有”烙位”的影响|(~A )将得出 -61 即 2 的补码形式 1100 0011，因为一个有符号的二进制数。|
|<<|二进制左移运算符。左边操作数的值按右边操作数指定的位数向左移动。|A << 2 将得出 240 即 1111 0000|
|>>|二进制右移运算符。左边操作数的值按右边操作数指定的位数向右移动。|A >> 2 将得出 15 即 1111|
|>>>|右移填零运算符。左边操作数的值按右边操作数指定的位数向右移动并且值用 0 填充|A >>>2 将得出 15 即 0000 1111|

## 逻辑操作符: 

|运算符     |描述   |例子|
|----------|:----------:|-----:|
|&&|叫做逻辑与运算符。如果两个操作数都不为 0，那么情况为真|(A && B) 为假|
|\|\||叫做逻辑或运算符。如果两个操作数中一个任何一个不为0那么情况为真。|(A \|\| B) 为真|
|!|叫做逻辑非运算符。用来颠倒操作数的逻辑状态。如果情况为真那么逻辑非运算符将是假。|!(A && B) 为真|


## 赋值操作符：

|运算符     |描述   |例子|
|----------|:----------:|-----:|
|=|简单的赋值运算符，将值从右边的操作数赋给左边的操作数。|C = A + B 将把 A + B 的值赋给 C|
|+=|加后赋值运算符，它将右边操作数加上左边的操作数并将结果赋给左边的操作数|C += A 和 C = C + A 相等|
|-=|减后赋值运算符，它将左边操作数减去右边的操作数并将结果赋给左边的操作数|C -= A 和 C = C - A 相等|
|*=|乘后赋值运算符，它用左边操作数倍增右边的操作数并将结果赋给左边的操作数|C *= A 和 C = C * A 相等|
|/=|除后赋值运算符，它用右边操作数去除左边的操作数并将结果赋给左边的操作数|C /= A 和 C = C / A 相等|
|%=|取模后赋值运算符，它使用两个操作数取模并将结果赋给左边的操作数|C %= A 和 C = C % A 相等|
|<<=|左移后赋值运算符|C <<= 2 和 C = C << 2 相同|
|>>=|右移后赋值运算符|C >>= 2 和 C = C >> 2 相同|
|&=|按位与后赋值运算符|C &= 2 和 C = C & 2 相同|
|^=|按位异或后赋值运算符|C ^= 2 和 C = C ^ 2 相同|
|\|=|按位或后赋值运算符|C \|= 2 和 C = C \| 2 相同|

## 混杂操作符
很少有其它的操作符有 Java 语言支持。  

## 条件操作符(?:):
条件操作符也以三元操作符为人所知。这个操作符由三个操作数组成并且被用来估计布尔表达式。操作符的目的是决定哪个值应该被赋给变量。操作符这样写：  
```
variable x = (expression) ? value if true : value if false
```
## instanceOf 操作符:  
这个操作符仅用于对象引用变量。操作符检查对象是否是一种特别类型的(class 类型或者 interface 类型)。instanceOf 操作符这样写:  
```
( Object reference variable ) instanceOf  (class/interface type)
```
## Java 操作符的优先级:  

|种类    |运算符   |关联性|
|----------|:----------:|-----:|
|后缀|() [] . (点操作符)|左到右|
|一元|++ - - ! ~|右到左|
|乘法|* / % |左到右|
|加法|+ - |左到右|
|移动|>> >>> <<|左到右|
|关系|> >= < <=|左到右|
|等式|== !=|左到右|
|按位与|&|左到右|
|按位异或|^|左到右|
|按位或|\||左到右|
|逻辑与|&&|左到右|
|逻辑或|\|\||左到右|
|条件|?:|右到左|
|赋值|= += -= *= /= %= >>= <<= &= ^= \|=|右到左|
|逗号|,|左到右|

## while 循环:
一个 while 循环是一个允许你重复一个任务一定数量的次数的控制结构。  

## 语法:
一个 while 循环的语法像这样:  
```
while(Boolean_expression)
{
   //Statements
}
```
## do...while 循环:
do...while 循环和 while 循环是类似的，除了 do...while 循环保证执行至少一次。  

## 语法:
do...while 的语法像这样:
```
do
{
   //Statements
}while(Boolean_expression);
```
## for 循环
for 循环是一个重复控制结构，允许你有效地写一个需要执行指定次数的循环。  

for 循环是有用的当你知道一个任务需要被重复多少次时。  

## 语法：
for 循环的语法像这样:  
```
for(initialization; Boolean_expression; update)
{
   //Statements
}
```
## Java 中增强的 for 循环:
Java 5 中增强的 for 循环被引进。这主要是为数组而用的。  

## 语法:
增强的 for 循环像这样:  
```
for(declaration : expression)
{
   //Statements
}
```

## break 关键字:
break 关键字被用来停止整个循环。break 关键字必须在任何循环中或者一个 switch 语句中使用。  

break 关键字将停止最内层的循环执行和开始执行在块后代码的下一行。  

## continue 关键字:
continue 关键字可以在任何控制结构的循环中被使用。它使循环立即跳转到循环的下一个迭代。  
-在一个 for 循环中，continue 关键字使控制流立即跳转到 update 语句。  
- 在一个 while 循环或者 do/while 循环中，控制流立即跳转到布尔表达式。  

## 语法:
continue 的语法在任何循环中是一条单独的语句:  
```
continue;
```
## if 语句:
if 语句由一个有一条或多条语句伴随的布尔表达式组成。  

## 语法:
if 语句的语法像这样:  
```
if(Boolean_expression)
{
   //Statements will execute if the Boolean expression is true
}
```
## if...else 语句:
if 语句可以后接一个可选的 else 语句，它当布尔表达式是错误时执行。  

## 语法:
if...else 的语法像这样:  
```
if(Boolean_expression){
   //Executes when the Boolean expression is true
}else{
   //Executes when the Boolean expression is false
}
```
## if...else if...else 语句:
if 语句可以后跟一个 可选的 else if...else 语句，它对于测试使用单独的 if...else if 语句的不同状况是很有用的。  

## 语法:  
if...else 的语法像这样：
```
if(Boolean_expression 1){
   //Executes when the Boolean expression 1 is true
}else if(Boolean_expression 2){
   //Executes when the Boolean expression 2 is true
}else if(Boolean_expression 3){
   //Executes when the Boolean expression 3 is true
}else {
   //Executes when the one of the above condition is true.
}
```

## 嵌入的 if...else 语句:  
嵌入 if...else 语句总是合法的。当使用 if，else if,else 语句时需要记住这几点:  
- if 可以有 0 个或者 1 个 else 并且它必须在任何 else if 之后。  
- if 可以有 0 到许多 else if 并且它们必须在 else 之前。  
- 一旦一个 else if 成功，剩余的 else if 和 else 将不会测试。  

## 语法:  
一个嵌入的 if...else 语法像以下这样:  
```
if(Boolean_expression 1){
   //Executes when the Boolean expression 1 is true
   if(Boolean_expression 2){
      //Executes when the Boolean expression 2 is true
   }
}
```

## switch 语句:  
switch 语句允许一个变量平等地用一系列的值进行测试。每一个值没成为一个 case,进行 switch 的变量将被每个 case 测试。  

## 语法:  
增强的 for 循环的语法像这样:  
```
switch(expression){
    case value :
       //Statements
       break; //optional
    case value :
       //Statements
       break; //optional
    //You can have any number of case statements.
    default : //Optional
       //Statements
}
```

## Java 方法:  
一个 Java 方法是组合到一起来执行一个操作的语句的集合。比如，当你调用 System.out.println 方法,系统确实为在控制台显示一条信息而执行了几条语句。  

总体来说，方法由以下语法:  
```
modifier returnValueType methodName(list of parameters) {
  // Method body;
}
```  
- **修饰符:**可选择的修饰符，告诉编译器如何调用方法。这定义了方法的入口类型。  
- **返回值:**方法会返回一个值。returnValueType 是方法返回的值的数据类型。一些方法执行所需的操作而不返回一个值。在这种情况下，returnValueType 就是关键字 void。  
- **方法名:**这是方法的实际名字。方法名和参数列一起构成了方法签名。  
- **参数:**参数就像占位符。当一个方法被调用，你将一个值传给参数。这个值被称为实际参数或参数。参数列表指的是方法参数的类型，顺序，和数量。参数是可选的；那就是说，方法可能不含参数。  
- **方法体：**方法体包含定义方法做什么的语句集合。  

## Java 类&对象
- **对象**-对象有状态和行为。例子:一条狗有状态：颜色，名字，品种以及行为-摇尾巴，吠，吃。一个对象是一个类的实例。 
- **类**-一个类能被定义成一个描述行为/状态的它所在类型的对象支持的模板/蓝图。   

一个类的样本像以下这样:  
```
public class Dog{
   String breed;
   int age;
   String color;

   void barking(){
   }
   
   void hungry(){
   }
   
   void sleeping(){
   }
}
```
一个类能含有任何以下的变量类型。
- **本地变量**-在方法，构造函数或者块内定义的变量被称为本地变量。变量将在方法内被声明和初始化并且变量将在当方法完成时被销毁。  
- **实例变量**-实例变量是类内但是在方法外的变量。这些变量当类被载入时被实例化。实例变量能在任何那个特定类的方法，构造函数或块内被访问。  
- **类变量**-类变量是在一个类中，在任何方法之外被声明的变量，伴随一个 static 关键字。  

## 异常处理:  
方法使用 try 和 catch 关键字的组合捕获异常。try/catch 块被放置在可能会生成异常的代码周围。有 try/catch 块的代码被称作受保护的代码，使用 try/catch 的语法像以下这样:  
```
try
{
   //Protected code
}catch(ExceptionName e1)
{
   //Catch block
}
```
## 多个 catch 块: 
一个 try 块后能跟多个 catch 块。多个 catch 块的语法像这样:  
```
try
{
   //Protected code
}catch(ExceptionType1 e1)
{
   //Catch block
}catch(ExceptionType2 e2)
{
   //Catch block
}catch(ExceptionType3 e3)
{
   //Catch block
}
```
## throws/throw 关键字:  
如果方法不处理检查异常，方法必须用 throws 关键字声明它。throw 关键字在方法签名的最后出现。  

你可以通过使用 throw 关键字抛出一个异常，可以是新实例化的或者刚刚捕获到的。尽量理解 throws 和 throw 关键字间的不同。  

## finally 关键字  
finally 关键字被用来创建一块跟在 try 块后的代码。finally 代码块总是执行，无论一个异常是否发生。  

使用 finally 块允许你允许运行你想要执行的任何 clean-type 语句，无论在受保护的代码中发生了什么。  

finally 块在 catch 块的末尾出现并有以下语法:  
```
try
{
   //Protected code
}catch(ExceptionType1 e1)
{
   //Catch block
}catch(ExceptionType2 e2)
{
   //Catch block
}catch(ExceptionType3 e3)
{
   //Catch block
}finally
{
   //The finally block always executes.
}
```
对 Java 编程语言的完整细节来说，建议查看我们的简单 [Java Tutorial](http://www.tutorialspoint.com/java/index.htm)
