# Java Numbers 类
   
通常情况下，当我们与数字打交道时，使用原始数据类型，如 byte，int，long，double 等。

### 示例

```
int i = 5000;
float gpa = 13.65;
byte mask = 0xaf;
```

然而，在开发中，我们会遇到需要使用对象而不是原始数据类型的情况。为了实现这个， Java 为每个原始数据类型提供包装类。  

所有的包装类 (Integer, Long, Byte, Double, Float, Short) 是抽象类 Number 的子类。   
  
![image](images/number_classes.jpg) 

这种包装是由编译器处理，这个过程称为装箱。因此，当一个原始数据类型被使用，当需要一个对象时，编译器将原始数据放入其包装类。同样地，编译器也能将对象取出返回到原始数据类型。Number 是 java.lang 包的一部分。 

这里是装箱和拆箱的一个例子：  

```
public class Test{

   public static void main(String args[]){
      Integer x = 5; // boxes int to an Integer object
      x =  x + 10;   // unboxes the Integer to a int
      System.out.println(x); 
   }
}
```

这将产生以下结果:  

```
15
```

当 x 被分配整数值，则编译器将整数放入箱中，因为 x 为整数对象。然后，x 被拆箱，以便它们可以被添加为整数。

## Number 方法

以下是对 Number 类实现的所有子类中实现的实例方法的列表：

|SN   |	                                     方法描述  |
|----:|----------------------------------------------:|
|1  |xxxValue() <br>   这个Number对象的值转换为XXX的数据类型并返回|
|2  |compareTo() <br>  把这个Number对象与参数做比较               |
|3  |equals() <br>     确定这个数字对象是否等于参数                  |
|4  |valueOf() <br>    返回一个Integer对象持有指定的原始值|
|5  |toString() <br>   返回表示指定的int或整数的值的String对象|
|6  |parseInt() <br>   此方法用于获取某个字符串的原始数据类型|
|7  |abs() <br>        返回参数的绝对值|
|8  |ceil() <br>       返回的最小整数大于或等于该参数。返回为double|
|9  |floor() <br>      返回的最大整数小于或等于该参数。返回为double|
|10 |rint() <br>      返回的整数，它是最接近值该参数值。返回为double|
|11 |round() <br>     返回最接近的long或者int，通过该方法的返回类型所指参数|
|12 |min() <br>       返回两个参数中较小的|
|13 |max() <br>       返回两个参数中较大的|
|14 |exp() <br>       返回自然对数的底数e，该参数的幂值|
|15 |log()  <br>      返回参数的自然对数|
|16 |pow() <br>       返回第一个参数的提高至第二个参数的幂值|
|17 |sqrt() <br>      返回参数的平方根|
|18 |sin() <br>       返回指定的double值的正弦值|
|19 |cos() <br>       返回指定的double值的余弦值|
|20 |tan() <br>       返回指定的double值的正切值|
|21 |asin()<br>       返回指定的double值的反正弦|
|22 |acos() <br>      返回指定的double值的反余弦值|
|23 |atan() <br>      返回指定的double值的反正切值|
|24 |atan2() <br>     将直角坐标(x,y)转换为极坐标(r,θ)并返回θ|
|25 |toDegrees() <br> 将参数转换为度|
|26 |toRadians() <br> 将参数转换为弧度|
|27 |random() <br>    返回一个随机数|

## 接下来是？ 

在下一节中，我们将学习 Character 类。将学习如何在 Java 中使用 Character 对象和基本数据类型 char。
