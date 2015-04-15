# Java - 序列化

Java 提供了一种机制，叫做对象序列化，这里对象被描述成一系列包括对象的数据以及有关对象的类型和在对象中存储的数据的类型的字节。  

在一个序列化的对象被写进文件之后，它能在文件中被读出并被反序列化为类型信息和表示对象的字节，并且它的数据可以被用来重新创建在内存中的对象。  

最让人印象深刻的是整个过程是 JVM 独立的，意味着一个对象能在一个平台上序列化，并能在在一个完全不同的平台上被反序列化。  

**ObjectInputStream** 和 **ObjectOutputStream** 类是包含序列化和反序列化对象的方法的高级别流。  

ObjectOutputStream 类含有许多写各种各样数据类型的写方法，但是其中一个方法尤其突出：

```
public final void writeObject(Object x) throws IOException
```

上述的方法序列化了一个对象并将它送入输出流。相同的，ObjectInputStream 类包含以下反序列化对象的方法：  

```
public final Object readObject() throws IOException, 
                                 ClassNotFoundException
```

这个方法检索流之外的下一个对象并且反序列化之。返回值是对象，所以你需要将它转换成正确的数据类型。  

为了论证序列化在 java 中是如何工作的，我将使用我们之前在书中讨论过的 Employee 类。假设我们有以下的实现 Serializable 的 Employee 类：

```
public class Employee implements java.io.Serializable
{
   public String name;
   public String address;
   public transient int SSN;
   public int number;
   public void mailCheck()
   {
      System.out.println("Mailing a check to " + name
                           + " " + address);
   }
}
```

注意到为使一个类被成功序列化，两个条件必须被满足：  
- 类必须实现 java.io.Serializable 类。  
- 类中所有的字段必须被序列化。如果一个字段没有被序列化，它必须被标记为瞬态的。  

如果你好奇地想知道 Java 标准类是否是可序列化的，可以查看下类的文档。测试是简单的：如果类实现了 java.io.Serializable，那它就是可序列化的；否则，它就不是。  

## 序列化一个对象 
ObjectOutputStream 类被用来序列化一个对象。下面的 SerializeDemo 程序实例化了一个 Employee 对象并且将它在一个文件中序列化。  

当程序被执行完毕后，一个名为 employee.ser 的文件就被创建了。程序不生成任何输出，但是研究代码并试图确定程序是在做什么。  

**注释：**当序列化一个对象到一个文件，在 java 中标准的规定是给予文件一个 .ser  的扩展。  

```
import java.io.*;

public class SerializeDemo
{
   public static void main(String [] args)
   {
      Employee e = new Employee();
      e.name = "Reyan Ali";
      e.address = "Phokka Kuan, Ambehta Peer";
      e.SSN = 11122333;
      e.number = 101;
      try
      {
         FileOutputStream fileOut =
         new FileOutputStream("/tmp/employee.ser");
         ObjectOutputStream out = new ObjectOutputStream(fileOut);
         out.writeObject(e);
         out.close();
         fileOut.close();
         System.out.printf("Serialized data is saved in /tmp/employee.ser");
      }catch(IOException i)
      {
          i.printStackTrace();
      }
   }
}

```

## 反序列化一个对象
下面的 DeserializeDemo 程序反序列化了一个在 SerializeDemo 对象中被创建的 Employee 对象。研究这个程序并且试图确定它的输出：
```
import java.io.*;
public class DeserializeDemo
{
   public static void main(String [] args)
   {
      Employee e = null;
      try
      {
         FileInputStream fileIn = new FileInputStream("/tmp/employee.ser");
         ObjectInputStream in = new ObjectInputStream(fileIn);
         e = (Employee) in.readObject();
         in.close();
         fileIn.close();
      }catch(IOException i)
      {
         i.printStackTrace();
         return;
      }catch(ClassNotFoundException c)
      {
         System.out.println("Employee class not found");
         c.printStackTrace();
         return;
      }
      System.out.println("Deserialized Employee...");
      System.out.println("Name: " + e.name);
      System.out.println("Address: " + e.address);
      System.out.println("SSN: " + e.SSN);
      System.out.println("Number: " + e.number);
    }
}
```

这将产生以下结果：
```
Deserialized Employee...
Name: Reyan Ali
Address:Phokka Kuan, Ambehta Peer
SSN: 0
Number:101
```

下面是一些需要注意的要点：  
- try/catch 块试图抓住 readObject() 方法声明的 ClassNotFoundException。为了使一个 JVM 能反序列化一个对象，它必须能找到类的字节代码。如果 JVM 在一个对象的反序列化过程中不能找到一个类，它将抛出 ClassNotFoundException。  
- 注意 readObject() 的返回值将参考 Employee。  
- 当对象被序列化时 SSN 字段的值是 11122333，但是因为字段是短暂的，值没有送入输出流。反序列化的 Employee 对象的 SSN 字段值是 0。

