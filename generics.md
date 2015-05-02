# Java - 泛型

如果我们可以写一个单独的能在一个整型数组，一个字符串数组或者一个任何类型支持排序的数组内排列元素的排序方法将会是很好的。  

Java `Generic` 方法和 generic 类让程序员可以用一种单独的方法声明，一系列有关的方法或者用一个单独的类声明来各自指定一系列有关的类型。  

Generic 也提供了编译时类型安全来允许程序员在编译时捕获无效的类型。  

使用 Java Generic 概念，我们可以写一个泛型方法来给对象数组排序，然后调用带有整型数组，double 型数组，字符串数组或其他的泛型方法来为数组元素排序。  

## 泛型方法

你可以写一个单独的可以被不同类型的参数调用的泛型方法声明。基于传给泛型方法的参数类型，编译器正确处理每个调用的方法。以下是定义泛型方法的规则:  
- 所有的泛型方法声明在方法的返回值之前(下一个例子中的<E>)有一个由尖括号分隔开的类型参数区域。(<and>)  
- 类型参数能被用来声明返回类型和作为传给泛型方法的参数类型的占位符，就是为人所知的真正的类型参数。  
- 一个泛型方法的主体像其他方法声明一样。注意到类型参数仅能代表引用类型，而不是原始类型(就像 int,double 和 char)。

### 示例

以下的例子说明了我们可以通过一个通用的方法来打印不同类型的数组:

```
public class GenericMethodTest
{
   // generic method printArray                         
   public static < E > void printArray( E[] inputArray )
   {
      // Display array elements              
         for ( E element : inputArray ){        
            System.out.printf( "%s ", element );
         }
         System.out.println();
    }

    public static void main( String args[] )
    {
        // Create arrays of Integer, Double and Character
        Integer[] intArray = { 1, 2, 3, 4, 5 };
        Double[] doubleArray = { 1.1, 2.2, 3.3, 4.4 };
        Character[] charArray = { 'H', 'E', 'L', 'L', 'O' };

        System.out.println( "Array integerArray contains:" );
        printArray( intArray  ); // pass an Integer array

        System.out.println( "\nArray doubleArray contains:" );
        printArray( doubleArray ); // pass a Double array

        System.out.println( "\nArray characterArray contains:" );
        printArray( charArray ); // pass a Character array
    } 
}
```

这将产生以下结果:

```
Array integerArray contains:
1 2 3 4 5 6

Array doubleArray contains:
1.1 2.2 3.3 4.4 

Array characterArray contains:
H E L L O
```

## 受限的类型参数

有时候你想要限制允许传给一个类型参数的类型种类。例如，操作数的方法可能仅仅想要接受 Number 的实例或者它的子类。这就是有限的类型参数。  

声明一个有限的类型参数，列举类型参数的名字，后面跟着扩展关键字和它的上界。

### 示例

下面的例子说明了如何使用扩展在一定意义上意味着“继承”(在类中)或是在“实现”(在接口中)。这个例子是返回三个 Comparable 对象中最大的泛型方法：  

```
public class MaximumTest
{
   // determines the largest of three Comparable objects
   public static <T extends Comparable<T>> T maximum(T x, T y, T z)
   {                      
      T max = x; // assume x is initially the largest       
      if ( y.compareTo( max ) > 0 ){
         max = y; // y is the largest so far
      }
      if ( z.compareTo( max ) > 0 ){
         max = z; // z is the largest now                 
      }
      return max; // returns the largest object   
   }
   public static void main( String args[] )
   {
      System.out.printf( "Max of %d, %d and %d is %d\n\n", 
                   3, 4, 5, maximum( 3, 4, 5 ) );

      System.out.printf( "Maxm of %.1f,%.1f and %.1f is %.1f\n\n",
                   6.6, 8.8, 7.7, maximum( 6.6, 8.8, 7.7 ) );

      System.out.printf( "Max of %s, %s and %s is %s\n","pear",
         "apple", "orange", maximum( "pear", "apple", "orange" ) );
   }
}
```

这将会产生以下结果:

```
Maximum of 3, 4 and 5 is 5

Maximum of 6.6, 8.8 and 7.7 is 8.8

Maximum of pear, apple and orange is pear
```

## 泛型类

泛型类的声明看起来像一个非泛型类的声明，除了类名后跟着一个类型参数区域。  

与泛型方法一样，一个泛型类的类型参数区域可以拥有一个或者更多的由逗号分隔的类型参数。这些类被称为参数化的类或是参数化的类型因为他们接受一个或更多的参数。  

### 示例

下面的例子说明了我们怎样定义一个泛型类:

```
public class Box<T> {

  private T t;

  public void add(T t) {
    this.t = t;
  }

  public T get() {
    return t;
  }

  public static void main(String[] args) {
     Box<Integer> integerBox = new Box<Integer>();
     Box<String> stringBox = new Box<String>();
    
     integerBox.add(new Integer(10));
     stringBox.add(new String("Hello World"));

     System.out.printf("Integer Value :%d\n\n", integerBox.get());
     System.out.printf("String Value :%s\n", stringBox.get());
  }
}
```

这将产生以下结果:

```
Integer Value :10

String Value :Hello World
```