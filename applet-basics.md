# Java Applet 基础

一个 Applet 是一个运行在网页浏览器上的 Java 程序。一个 Applet 可以使一个全功能的 Java 应用程序因为它在处理上拥有整个 Java API。  

在一个 Applet 和一个独立的 Java 应用程序间有一些重要的不同，包括以下方面：
  
- 一个 Applet 是继承  java.applet.Applet 类的一个 Java 类。
- main() 方法不在 Applet 上被调用，并且一个 applet 类将不定义 main()。  
- Applet 程序被设计嵌入到 HTML 页面中。
- 当一个用户查看一个带有 applet 的 HTML 页面，applet 的代码将被下载到用户的机器中。  
- 需要 JVM 来查看一个 applet。JVM 可以是一个网页浏览器的一个插件，也可以是单独的运行环境。  
- 用户机器上的 JVM 创建了 applet 类的实例并且在 applet 的生命周期中调用不同的方法。
- Applets 有网页浏览器实施的严格的安全规则。一个 applet 程序的安全性常常被称作沙箱安全，这是将 applet 比作一个正在沙箱中的，必须遵守许多规则的孩子。 
- 其他 applet 需要的类可以在一个单独的 Java Archive(JAR) 文件中下载。  

## 一个 Applet 的生命周期

Applet 类中的四个方法给了你构建 applet 程序时的框架：  
- **init：** 这个方法适用于你的 applet 程序所需要的任何初始化。它在 applet 标记中的参数标签被处理后被调用。  
- **start：** 这个方法在浏览器调用 init 方法后被自动调用。它也在无论何时使用者在去其他页面后返回到包含 applet 的页面时被调用。    
- **stop：** 这个方法在使用者离开有 applet 所在的页面时被自动调用。因此，它在同一个 applet 中能被重复调用。 
- **destroy：** 这个方法仅当浏览器正常关闭时被自动调用。因为 applet 程序是生存在 HTML 页面上的，你不应该在使用者离开有 applet 的网页后留下资源。  
- **paint：** 在 start() 方法之后被立即调用，或是在 applet 需要在浏览器上重现它自身的任何时候。paint() 方法实际上是继承自 java.awt。  

## 一个 “Hello,World” Applet

以下是一个简单的叫做 HelloWorldApplet.java 的 applet 程序：  

```
import java.applet.*;
import java.awt.*;

public class HelloWorldApplet extends Applet
{
   public void paint (Graphics g)
   {
      g.drawString ("Hello World", 25, 50);
   }
}
```

这些引入的语句把类带入我们的 applet 类的范围内：  
- java.applet.Applet.
- java.awt.Graphics.  

没有那些引入的语句，Java 编译器将不会认出 applet 类所指的 Applet 和 Graphics 类。  

## Applet 类

每一个 applet 类都是 java.applet.Applet 类的延伸。基本的 Applet 类提供了一个派生的 Applet 类用来调用从浏览器获取信息和服务的方法。  

这还包括了做以下事情的方法：  
- 获得 applet 参数
- 获得包含 applet 的 HTML 文件的网络地址
- 获得 applet 类目录的网络地址
- 在浏览器中打印状态信息
- 获取一个图像
- 获取一段音频剪辑
- 播放一段音频剪辑
- 调整 applet 的大小

此外，Applet 类通过观察器和浏览器获得有关 applet 的信息和控制 applet 的执行来提供一个接口。观察者可能：
- 需要作者的信息，版本和 applet 的版权
- 需要 applet 识别的参数的描述
- 初始化 applet
- 销毁 applet
- 开始 applet 的执行
- 停止 applet 的执行  

## 调用一个 Applet 程序

一个 applet 可能被一个 HTML 文件中嵌入的指令文件调用并通过一个 applet 观察器或者支持 Java 的浏览器查看文件。  

<applet> 标签是在一个 HTML 文件中嵌入一个 applet 的基础。以下是调用“Hello,World” applet 的例子：

```
<html>
<title>The Hello, World Applet</title>
<hr>
<applet code="HelloWorldApplet.class" width="320" height="120">
If your browser was Java-enabled, a "Hello, World"
message would appear here.
</applet>
<hr>
</html>
```
 
<applet> 标签的 code 属性是需要的。它指定 Applet 类运行。宽度和高度也是需要来规定 applet 运行的面板的初始大小。applet 指令必须用 </applet> 标签结束。  

如果一个 applet 需要参数，值可能通过在 <applet> 和 </applet> 间添加 <param> 标签来传给参数。  

Java 不支持的浏览器不处理 <applet> 和 </applet>。因此，任何出现在标签之间的，和 applet 无关的，在 Java 不支持的浏览器内都是可见的。  

观察器和浏览器在文件的地址寻找编译好的 Java 代码。否则指定，像下面这样使用 <applet> 标签的 codebase 属性：

```
<applet codebase="http://amrood.com/applets"
code="HelloWorldApplet.class" width="320" height="120">
```

如果一个 applet 常驻在一个包内而不是默认，保存的包必须规定在 code 属性内，使用句点字符（.）来分离包/类成分：

```
<applet code="mypackage.subpackage.TestApplet.class" 
           width="320" height="120">
```

## 获得 Applet 参数

下面的例子展示了如何进行 applet 响应设置文档中指定的参数。这个 applet 展示了黑色和第二种颜色的棋盘式样式。  

第二种颜色和每个方格的大小会由文件中的 applet 的参数所指定。  

CheckerApplet 在 init() 方法中获得它的参数。它也能在 paint() 方法中获得它的参数。然而，在 applet 一开始就获得值并保存设置，而不是在每次刷新时，是方便有效的。

applet 观察器或者浏览器在每一个 applet 运行时调用 init() 方法。观察器在加载 applet 程序后立即调用 init() 方法。(Applet.init() 实现后不做任何事)覆写默认的实现来插入自定义初始化代码。  

Applet.getParameter() 方法获得一个给定参数名称的参数(参数的值总是一个字符串)。如果值是数值的或者其他非字符数据，字符串必须被解析。  

以下是 CheckerApplet.java 的构架：  

```
import java.applet.*;
import java.awt.*;
public class CheckerApplet extends Applet
{
   int squareSize = 50;// initialized to default size
   public void init () {}
   private void parseSquareSize (String param) {}
   private Color parseColor (String param) {}
   public void paint (Graphics g) {}
}
```

这里是 CheckerApplet 的 init() 和私有的 parseSquareSize() 方法：
  
```
public void init ()
{
   String squareSizeParam = getParameter ("squareSize");
   parseSquareSize (squareSizeParam);
   String colorParam = getParameter ("color");
   Color fg = parseColor (colorParam);
   setBackground (Color.black);
   setForeground (fg);
}
private void parseSquareSize (String param)
{
   if (param == null) return;
   try {
      squareSize = Integer.parseInt (param);
   }
   catch (Exception e) {
     // Let default value remain
   }
}
```

applet 调用 parseSquareSize() 来解析 squareSize 参数。parseSquareSize() 调用 library 方法 Integer.parseInt(),它解析了一个字符串并返回一个整型。Integer.parseInt() 每当它的参数无效时就抛出一个异常。  

因此，parseSquareSize() 捕获一个异常，而不是允许 applet 因为错误的输入失效。  

applet 调用 parseColor() 来解析 color 参数成一个 Color 值。parseColor() 进行了一系列的字符串比较来将参数值和一个预定义的颜色进行匹配。你需要实现这些方法来进行 applet 工作。

## 指定 Applet 参数

以下是一个有 CheckerApplet 嵌入的 HTML 文件的例子。HTML 文件通过 <param> 标签的方法指定两个 applet 的参数。

```
<html>
<title>Checkerboard Applet</title>
<hr>
<applet code="CheckerApplet.class" width="480" height="320">
<param name="color" value="blue">
<param name="squaresize" value="30">
</applet>
<hr>
</html>
```

**注意：** 参数名字不区分大小写

## 应用程序转换为 Applet

将一个图形化的 Java 应用程序(那就是，一个使用 AWT 并且你能用 Java 程序启动器启动的应用程序)转换为一个可以嵌入到一个网页中的 applet 程序是简单的。  

这是将应用程序转换为 applet 的指定步骤。
- 制作一个有正确的标签的 HTML 网页来载入 applet 代码。
- 提供一个 JApplet 类的子类。使这个类公开。否则，applet 不能不载入。
- 消除应用程序中的 main 方法。不要为应用程序构建一个框架窗口。你的应用程序将在浏览器内被展示。
- 将任何初始化代码从框架窗口构造函数移动到 applet 的 init 方法。你不需要精确地构造 applet 对象。浏览器为你初始化了并且调用 init 方法。  
- 移除对 setSize 的调用；对 applet 来说，调整宽度和高度的参数在 HTML 中已经做好了。  
- 移除对 setDefaultCloseOperation 的调用。一个 applet 不能关闭；它在浏览器退出时消失。  
- 如果应用程序调用 setTitle,消除了对方法的调用。Applet 不能拥有标题栏。(当然你可以用 HTML 标题标签来给网页定义自身标签)
- 不要调用 setVisible(true)。applet 自动设置了。  

## 事件处理

applet 从 Container 类中继承了一组事件处理的方法。Container 类为解决特殊的时间类型，定义了几种方法，比如 processKeyEvent 和 processMouseEvent，和一个万能的叫做 processEvent 的方法。  

为了使一个事件生效，applet 必须覆写正确的事件方法。  

```
import java.awt.event.MouseListener;
import java.awt.event.MouseEvent;
import java.applet.Applet;
import java.awt.Graphics;

public class ExampleEventHandling extends Applet 
			 implements MouseListener {

    StringBuffer strBuffer;

    public void init() {
	addMouseListener(this);
	strBuffer = new StringBuffer();
        addItem("initializing the apple ");
    }

    public void start() {
        addItem("starting the applet ");
    }

    public void stop() {
        addItem("stopping the applet ");
    }

    public void destroy() {
        addItem("unloading the applet");
    }

    void addItem(String word) {
        System.out.println(word);
        strBuffer.append(word);
        repaint();
    }

    public void paint(Graphics g) {
	//Draw a Rectangle around the applet's display area.
        g.drawRect(0, 0, 
		   getWidth() - 1,
		   getHeight() - 1);

	//display the string inside the rectangle.
        g.drawString(strBuffer.toString(), 10, 20);
    }

   
    public void mouseEntered(MouseEvent event) {
    }
    public void mouseExited(MouseEvent event) {
    }
    public void mousePressed(MouseEvent event) {
    }
    public void mouseReleased(MouseEvent event) {
    }

    public void mouseClicked(MouseEvent event) {
	addItem("mouse clicked! ");
    }
}
```

现在，让我们像这样调用下面的 applet:  

```
<html>
<title>Event Handling</title>
<hr>
<applet code="ExampleEventHandling.class" 
width="300" height="300">
</applet>
<hr>
</html>
```

最初，applet 将会展示 “初始化 applet,开始 applet”。然后一旦你点击长方形内的 “鼠标点击” 将会显示。  

基于上面的例子，这里是 applet 例子:[Applet Example](http://www.tutorialspoint.com/java/event.htm)

## 显示图像

一个 applet 能显示 GIF，JPEG，BMP 和其它格式的图像。为了显示 applet 中的图像，你可以使用在 java.awt.Graphics 类中的 drawImage() 方法。  

以下是展示所有步骤来显示图像的例子：  

```
import java.applet.*;
import java.awt.*;
import java.net.*;
public class ImageDemo extends Applet
{
  private Image image;
  private AppletContext context;
  public void init()
  {
      context = this.getAppletContext();
      String imageURL = this.getParameter("image");
      if(imageURL == null)
      {
         imageURL = "java.jpg";
      }
      try
      {
         URL url = new URL(this.getDocumentBase(), imageURL);
         image = context.getImage(url);
      }catch(MalformedURLException e)
      {
         e.printStackTrace();
         // Display in browser status bar
         context.showStatus("Could not load image!");
      }
   }
   public void paint(Graphics g)
   {
      context.showStatus("Displaying image");
      g.drawImage(image, 0, 0, 200, 84, null);
      g.drawString("www.javalicense.com", 35, 100);
   }  
}
```

现在，让我们像这样调用这个 applet:  

```
<html>
<title>The ImageDemo applet</title>
<hr>
<applet code="ImageDemo.class" width="300" height="200">
<param name="image" value="java.jpg">
</applet>
<hr>
</html>
```

基于上面的例子，这里是 applet 例子：[Applet Example](http://www.tutorialspoint.com/java/ImageDemo.htm)。  

## 播放音频

一个 applet 能播放由 java.applet 包内的 AudioClip 接口表示的音频。AudioClip 接口有三个方法，包括：
- **public void play()：** 从开始时，播放一次音频片段。  
- **public void loop()：** 使音频片段持续重复播放。
- **public void stop()：** 停止播放音频片段。  

为了获得一个 AudioClip 对象，你必须调用 Applet 类的 getAudioClip() 方法。getAudioClip() 方法立刻返回，无论 URL 是否解决一个真正的音频片段。当播放音频片段时它才被下载。  

以下是播放音频的所有步骤的一个例子：

```
import java.applet.*;
import java.awt.*;
import java.net.*;
public class AudioDemo extends Applet
{
   private AudioClip clip;
   private AppletContext context;
   public void init()
   {
      context = this.getAppletContext();
      String audioURL = this.getParameter("audio");
      if(audioURL == null)
      {
         audioURL = "default.au";
      }
      try
      {
         URL url = new URL(this.getDocumentBase(), audioURL);
         clip = context.getAudioClip(url);
      }catch(MalformedURLException e)
      {
         e.printStackTrace();
         context.showStatus("Could not load audio file!");
      }
   }
   public void start()
   {
      if(clip != null)
      {
         clip.loop();
      }
   }
   public void stop()
   {
      if(clip != null)
      {
         clip.stop();
      }
   }
}
```

现在，让我们调用这个 applet:  

```
<html>
<title>The ImageDemo applet</title>
<hr>
<applet code="ImageDemo.class" width="0" height="0">
<param name="audio" value="test.wav">
</applet>
<hr>
</html>
```

你可以使用你电脑的 test.wav 来测试上面的例子。
