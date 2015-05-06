# Java 文件注释

Java 语言支持三种注释形式：  

|注释      |描述   |
|----------|:----------|:-----|
|/\*text\*/ |编译器忽略 /* 到 */ 的所有东西|
|//text |编译器忽略从 // 到一行末尾的所有东西|
|/\*\*<br>documentation<br>*/ |这是文档注释并且通常而言它被叫做 doc comment。JDK javadoc 工具当准备自动准备生成文件时使用 doc comment |   

这个指导是关于解释 Javadoc 的。我们将看到我们怎样能利用 Javadoc 来为我们的 Java 代码生成有用的文件。  

## 什么是 Javadoc？

Javadoc 是 JDK 附带的一个工具，它被用来生成从需要预定义格式的文档的 Java 源代码至 HTML 格式的 Java 代码文件。  

以下是一个简单的例子，其中红色部分代表 Java 注释：  

```
/**
* The HelloWorld program implements an application that
* simply displays "Hello World!" to the standard output.
*
* @author  Zara Ali
* @version 1.0
* @since   2014-03-31 
*/
public class HelloWorld {
    public static void main(String[] args) {
        // Prints Hello, World! on standard output.
        System.out.println("Hello World!");
    }
}
```

你可以将需要的 HTML 标签包括在描述部分内，比如，下面的例子利用 \<h1\>...\</h1\> 来定义头部和 \<p\> 被用来创建段落间隔：

```
/**
* <h1>Hello, World!</h1>
* The HelloWorld program implements an application that
* simply displays "Hello World!" to the standard output.
* <p>
* Giving proper comments in your program makes it more
* user friendly and it is assumed as a high quality code.
* 
*
* @author  Zara Ali
* @version 1.0
* @since   2014-03-31 
*/
public class HelloWorld {
    public static void main(String[] args) {
        // Prints Hello, World! on standard output.
        System.out.println("Hello World!");
    }
}
```

## Javadoc 标签

Javadoc 标签是 Javadoc 认可的关键字，它定义了下面信息的类型。  

Javadoc 工具认可下面的标签： 

|标签      |描述   |语法   |
|:----------|:----------|:-----|
|@author|添加类的作者|@author name-text|
|{@code}|不把文本转换成 HTML 标记和嵌套的 Java 标签而用代码字体展示它|{@code text}|
|{@docRoot}|表示从任何生成页面到生成文档的根目录的相对路径|{@docRoot}|
|@deprecated|添加一个注释暗示 API 应该不再被使用|@deprecated deprecated-text|
|@exception|用类名和描述文本给生成的文档添加一个副标题 |@exception class-name description|
|{@inheritDoc}|从最近的可继承的类或可实现的接口继承注释 |Inherits a comment from the immediate surperclass.|
|{@link}|用指向特定的包，类或者一个引用类的成员名的文档的可见文本标签插入在线链接|{@link package.class#member label}|
|{@linkplain}|和{@link}相同，除了链接的标签用纯文本标示而不是代码字体|{@linkplain package.class#member label}|
|@param|给“参数”区域添加一个有特定参数名且后跟着特定描述的参数|@param parameter-name description|
|@return|添加一个有描述文本的“Returns”区域|@return description|
|@see|添加带有链接或者指向引用的文本入口的标题“See Also”|@see reference|
|@serial|在默认的序列化字段的文本注释中使用|@serial field-description | include | exclude|
|@serialData|记录由 writeObject( ) 或 writeExternal( )方法所写的数据|@serialData data-description|
|@serialField|记录一个 ObjectStreamField 成分|@serialField field-name field-type field-description|
|@since|给生成的文档添加一个带有特定 since 文本的"Since"标题|@since release|
|@throws|@throw 和 @exception 标签是同义词|@throws class-name description|
|{@value}|当{@value}被用在一个静态字段的文本注释中，它展示了那个常量的值|{@value package.class#field}|
|@version|当 -version 选项被使用时用特定的 version w文本给生成的文本添加一个“Version”副标题|@version version-text|

### 示例

下面的程序使用一些重要的标签来做文档注释。你可以基于你的需求利用其它的标签。  

关于 AddNum 类的文档将由 HTML 文件 AddNum.html 创建，但是同时一个名为 index.html 的主文件也将被创建。 
 
```
import java.io.*;

/**
* <h1>Add Two Numbers!</h1>
* The AddNum program implements an application that
* simply adds two given integer numbers and Prints
* the output on the screen.
* <p>
* <b>Note:</b> Giving proper comments in your program makes it more
* user friendly and it is assumed as a high quality code.
*
* @author  Zara Ali
* @version 1.0
* @since   2014-03-31
*/
public class AddNum {
   /**
   * This method is used to add two integers. This is
   * a the simplest form of a class method, just to
   * show the usage of various javadoc Tags.
   * @param numA This is the first paramter to addNum method
   * @param numB  This is the second parameter to addNum method
   * @return int This returns sum of numA and numB.
   */
   public int addNum(int numA, int numB) {
      return numA + numB;
   }

   /**
   * This is the main method which makes use of addNum method.
   * @param args Unused.
   * @return Nothing.
   * @exception IOException On input error.
   * @see IOException
   */
   public static void main(String args[]) throws IOException
   {

      AddNum obj = new AddNum();
      int sum = obj.addNum(10, 20);

      System.out.println("Sum of 10 and 20 is :" + sum);
   }
}
```

现在，处理使用 Javadoc 的 AddNum.java 文件：

```
$ javadoc AddNum.java
Loading source file AddNum.java...
Constructing Javadoc information...
Standard Doclet version 1.7.0_51
Building tree for all the packages and classes...
Generating /AddNum.html...
AddNum.java:36: warning - @return tag cannot be used in method with void return type.
Generating /package-frame.html...
Generating /package-summary.html...
Generating /package-tree.html...
Generating /constant-values.html...
Building index for all the packages and classes...
Generating /overview-tree.html...
Generating /index-all.html...
Generating /deprecated-list.html...
Building index for all classes...
Generating /allclasses-frame.html...
Generating /allclasses-noframe.html...
Generating /index.html...
Generating /help-doc.html...
1 warning
$
```

你可以在这检查所有的生成的文档：[AddNum](http://www.tutorialspoint.com/java/index.html)。如果你正在使用 JDK 1.7 那么 Javadoc 不生成 **stysheet.css**，所以我建议从 [http://docs.oracle.com/javase/7/docs/api/stylesheet.css](http://docs.oracle.com/javase/7/docs/api/stylesheet.css) 下载并使用标准的 stylesheet。
