#Java决策制定  
在Java中有两种类型的决策语句，它们分别是：  
* if 语句
* switch 语句

## if 语句:  
if语句由一个布尔表达式后跟一个或多个语句组成。  
## 语法:  
if语句的语法是：  
```
if(Boolean_expression)
{
   //Statements will execute if the Boolean expression is true
}
```
如果布尔表达式的值为 true，那么代码里面的块if语句将被执行。如果不是true，在if语句（大括号后）结束后的第一套代码将被执行。  
##示例：
```
public class Test {

   public static void main(String args[]){
      int x = 10;

      if( x < 20 ){
         System.out.print("This is if statement");
      }
   }
}
```
这将产生以下结果：  
```
This is if statement
``` 

##if...else 语句:  
任何if 语句后面可以跟一个可选的 else 语句，当布尔表达式为 false，语句被执行。

##语法:  
if...else 的语法是:  
```
if(Boolean_expression){
   //Executes when the Boolean expression is true
}else{
   //Executes when the Boolean expression is false
}
```
## 示例：  
```
public class Test {

   public static void main(String args[]){
      int x = 30;

      if( x < 20 ){
         System.out.print("This is if statement");
      }else{
         System.out.print("This is else statement");
      }
   }
}
```
这将产生以下结果：  
```
This is else statement
```

## if...else if...else 语句:  
if后面可以跟一个可选的 else if...else语句，在测试不同条件下单一的if语句和else if语句是非常有用的。  
当使用 if , else if , else 语句时有几点要牢记。  
* 一个if语句可以有0个或一个 else语句 且它必须在else if语句的之后。
* 一个if语句 可以有0个或多个 else if语句且它们必须在else语句之前。
* 一旦 else if语句成功, 余下else if语句或else语句都不会被测试执行。  

##语法:  
if...else 的语法是:  
```
if(Boolean_expression 1){
   //Executes when the Boolean expression 1 is true
}else if(Boolean_expression 2){
   //Executes when the Boolean expression 2 is true
}else if(Boolean_expression 3){
   //Executes when the Boolean expression 3 is true
}else {
   //Executes when the none of the above condition is true.
}
```
##示例:
```
public class Test {

   public static void main(String args[]){
      int x = 30;

      if( x == 10 ){
         System.out.print("Value of X is 10");
      }else if( x == 20 ){
         System.out.print("Value of X is 20");
      }else if( x == 30 ){
         System.out.print("Value of X is 30");
      }else{
         System.out.print("This is else statement");
      }
   }
}
```
这将产生以下结果：  
```
Value of X is 30
```
## 嵌套 if...else 语句:  
它始终是合法的嵌套if-else语句，这意味着你可以在另一个if或else if语句中使用一个if或else if语句。

## 语法:  
嵌套 if...else 的语法如下：  
```
if(Boolean_expression 1){
   //Executes when the Boolean expression 1 is true
   if(Boolean_expression 2){
      //Executes when the Boolean expression 2 is true
   }
}
```
因为我们有嵌套的if语句，所以可以用类似的方式嵌套 else if...else，。  

## 示例:  
```
public class Test {

   public static void main(String args[]){
      int x = 30;
      int y = 10;

      if( x == 30 ){
         if( y == 10 ){
             System.out.print("X = 30 and Y = 10");
          }
       }
    }
}
```
这将产生以下结果：  
```
X = 30 and Y = 10
```
## switch 语句:  
switch 语句允许一个变量来对一系列值得相等性进行测试。每个值被称为一case，并且被启动的变量会为每一个case检查。 

## 语法:  
增强的 for循环的语法是：  
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
以下规则适用于switch语句：  
*	在switch语句中使用的变量只能是一个字节，short，int或char。
*	在一个switch语句中可以有任何数量的case语句。每个case后跟着即将被比较的值和一个冒号。
*	对于 case 的值必须是相同的数据类型作为开关变量，它必须是一个常量或文字。
*	当被启动了的变量与case是相等的，那case后的语句将执行，一直到 break 为止。
*	当达到一个break语句，switch 终止，并且控制流跳转到跟着switch语句的下一行。
*	不是每一个case需要包含一个break。如果没有出现break，控制流将贯穿到后面的case直到 break 为止。
*	switch语句可以有一个可选默认 case ，它必须出现在 switch 的结束处。在执行一项任务时没有任何case是真，那默认case可被使用。在默认case中不需要break。 

## 示例：  
```
public class Test {

   public static void main(String args[]){
      //char grade = args[0].charAt(0);
      char grade = 'C';

      switch(grade)
      {
         case 'A' :
            System.out.println("Excellent!"); 
            break;
         case 'B' :
         case 'C' :
            System.out.println("Well done");
            break;
         case 'D' :
            System.out.println("You passed");
         case 'F' :
            System.out.println("Better try again");
            break;
         default :
            System.out.println("Invalid grade");
      }
      System.out.println("Your grade is " + grade);
   }
}
```
编译并运行上面使用各种命令行参数的程序。这将产生以下结果：  
```
$ java Test
Well done
Your grade is a C
$
```
## 接下来是？  
下一章讨论了有关Number类（在java.lang包中）以及Java语言及其子类。  
我们将寻找到一些使用这些类的实例化，而不是原始数据类型，以及类如格式化，还有当你使用Number需要知道的数学函数。






