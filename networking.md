# Java 网络编程

术语网络编程指编写跨多种设备（电脑）执行的，设备使用一个网络互相连接的程序。  

J2SE API 的 java.net 包包含了一个类的集合和提供底层通信细节的接口，允许你编写专注解决即将到来的问题的程序。  

java.net 包为两种常用的网络协议提供支持：  
- **TCP：** TCP 代表传输控制协议，允许两个应用程序间的可靠通信。TCP 通常在因特网协议上被使用，这被称为 TCP/IP。  
- **UDP：** UDP 代表用户数据报协议，一个无连接的允许应用程序间数据包传输的协议。  

本教程给以下两个主题提供更好的理解：  
- **套接字编程：** 这是在网络中最广泛使用的概念并且被很详细地解释。  
- **URL 处理：** 这将被个别地解释。点击这里来学习 java 语言中的 [URL 处理](http://www.tutorialspoint.com/java/java_url_processing.htm)。  

## 套接字编程

套接字利用TCP在两台电脑间提供通信机制。一个客户端程序在通信最后创建一个套接字并努力连接服务器套接字。  

当连接建立时，服务器在通信结束时创建一个套接字对象。客户端和服务器现在可以通过从套接字读或者写来交流。  

java.net.Socket 类代表一个套接字，而且 java.net.ServerSocket 类为服务器程序提供了一种机制来监听客户端并和它们建立连接。  

以下步骤发生在两台电脑使用套接字建立TCP连接时：  
- 服务器实例化一个 ServerSocket 对象，指示通信将产生在哪个端口号；  
- 服务器调用 ServerSocket 类的 accept() 方法。这个方法等待直到一个客户端在给定的端口上连接到服务器；  
- 在服务器等待后，一个客户端实例化一个 Socket 对象，指定服务器名称和连接的端口号；   
- Socket 类的构造函数努力将客户端连接到指定的服务器和端口号。如果通信建立，客户端现在就拥有了一个能和服务器通信的 Socket 对象；  
- 在服务器端，accept() 方法在服务器上返回一个连接到客户端套接字的新的套接字。  

在连接建立后，通信可以使用 I/O 流产生。每个套接字都有一个输出流和一个输入流。客户端的输出流连接到服务器端的输入流，客户端的输入流连接到服务器端的输出流。  

TCP是一个双向的通信协议，所以数据可以在两个流同时发送。由以下提供完整的方法的类来实现套接字。  

## ServerSocket 类方法

java.net.ServerSocket 类被服务器应用程序使用来获得一个端口和监听客户端请求。  

ServerSocket 类有四个构造函数：

| SN        | 方法描述   |  
|----------|:----------:|-----:|
|1 | **public ServerSocket(int port) throws IOException**<br>尝试创建一个连接到指定端口的服务器套接字。如果端口已经连接到另一个应用程序那么将产生一个异常。|
|2 |**public ServerSocket(int port, int backlog) throws IOException**<br>和前一个构造函数相同，backlog 参数指定了在等待队列中有多少传入的客户端要存储|
|3 |**public ServerSocket(int port, int backlog, InetAddress address) throws IOException**<br>和前一个构造函数相同，InetAddress 参数指定了本地捆绑的IP地址。InetAddress 用于有多个 IP 地址的服务器，允许服务器指定它的哪个 IP 地址 来接收客户端请求。|
|4 |**public ServerSocket() throws IOException**<br>创建一个为绑定服务器的套接字。当使用这个构造函数时，当你准备好绑定服务器套接字时使用 bind()方法。|

如果 ServerSocket 的构造函数不抛出一个异常，这意味着你的应用程序已经成功地绑定到特定的端口并且准备好客户端的请求了。  

这里是一些 ServerSocket 类的常见方法：  

| SN        | 方法描述   |  
|----------|:----------:|-----:|
|1 |**public int getLocalPort()**<br>返回服务器套接字正在监听的端口。如果你在构造函数中传入 0 作为端口号这个方法会是有用的，它会让服务器为你找一个端口。|
|2 |**public Socket accept() throws IOException**<br>等待一个即将到来的客户端。这个方法直到或者一个客户端连接到特定端口服务器，或者套接字到时为止时阻塞，假设超时的值已经使用 setSoTimeout() 方法设置了。否则，这个方法将无限期阻塞。|
|3 |**public void setSoTimeout(int timeout)**<br>把超时的值设为服务器套接字在 accept() 内等待客户端的时间。|
|4 |**public void bind(SocketAddress host, int backlog)**<br>将套接字绑定在特定的服务器和 SocketAddress 对象的端口上。如果你使用无参数的构造函数实例化一个 ServerSocket 对象，使用这个方法。|
 
当 ServerSocket 调用  accept() 方法直到一个客户端连接才返回。在一个客户端确实连接后，ServerSocket 在一个未指定的端口上创建一个新的套接字，并返回一个新套接字的引用。一个 TCP 连接现在就存在于客户端和服务器间了，通信就可以开始了。  

## Socket 类方法

java.net.Socket 类方法代表客户端和服务器都用来互相通信的套接字。客户端通过实例化而拥有一个 Socket 对象，然而服务器从 accept() 方法的返回值获得一个 Socket 对象。  

Socket 类有5个客户端用来连接到服务器的构造函数：  

| SN        | 方法描述   |  
|----------|:----------:|-----:|
|1 |**public Socket(String host, int port) throws UnknownHostException, IOException.**<br>这个方法努力连接到特定端口指定的服务器。如果这个构造函数不抛出一个异常，连接就是成功的并且客户端将会连接到服务器。|
|2 |**public Socket(InetAddress host, int port) throws IOException**<br>这个方法和之前的构造函数相同，除了主机由一个 InetAddress 对象表示。|
|3 |**public Socket(String host, int port, InetAddress localAddress, int localPort) throws IOException.**<br>连接到指定的主机和端口，在指定地址和端口上的本地主机创建一个套接字。|
|4 |**public Socket(InetAddress host, int port, InetAddress localAddress, int localPort) throws IOException.**<br>这个方法和前一个构造函数相同，除了主机由一个 InetAddress 对象而不是一个 String 表示。|
|5 |**public Socket()**<br>创建一个不连接的套接字。使用 connect() 方法来连接这个套接字到服务器。|

当套接字构造函数返回时，它并不简单地实例化一个 Socket 对象，它实际上试图连接到指定的服务器和端口。  

在 Socket 类中一些有趣的方法列举在此。注意客户端和服务器都有一个 Socket 对象，所以这些方法都能被客户端或者服务器调用。

| SN        | 方法描述   |  
|----------|:----------:|-----:|
|1 |**public void connect(SocketAddress host, int timeout) throws IOException**<br>这个方法将套接字连接到特定的主机。这个方法仅当你使用无参数的构造函数实例化 Socket 时才需要。|
|2 |**public InetAddress getInetAddress()**<br>这个方法返回其套接字连接的其他电脑的地址。|
|3 |**public int getPort()**<br>返回远端的机器上套接字绑定的端口。|
|4 |**public int getLocalPort()**<br>返回本地机器上套接字绑定的端口。|
|5 |**public SocketAddress getRemoteSocketAddress()**<br>返回远程套接字的地址
|6 |**public InputStream getInputStream() throws IOException**<br>返回套接字的输入流。输入流连接到远程套接字的输出流。|
|7 |**public OutputStream getOutputStream() throws IOException**<br>返回套接字的输出流。输出流连接到远程套接字的输入流。|
|8 |**public void close() throws IOException**<br>关闭套接字，这使得这个 Socket 对象不再能够连接到任何服务器。|


## InetAddress 类方法  

这个类表示一个网络协议（IP）的地址。这些是在做套接字编程时将会用到的有用的方法：  

| SN        | 方法描述   |  
|----------|:----------:|-----:|
|1 |**static InetAddress getByAddress(byte[] addr)**<br>考虑到原始的 IP 地址，返回一个 InetAddress 对象。|
|2 |**static InetAddress getByAddress(String host, byte[] addr)**<br>基于提供的主机名和 IP 地址创建一个 InetAddress。|
|3 |**static InetAddress getByName(String host)**<br>考虑到主机名，决定一个主机的 IP 地址。|
|4 |**String getHostAddress()**<br>用文本表示返回的 IP 地址字符串。|
|5 |**String getHostName()**<br>获得这个 IP 地址的主机名。|
|6 |**static InetAddress InetAddress getLocalHost()**<br>返回本地主机。|
|7 |**String toString()**<br>将 IP 地址转换为字符串。|

## 套接字客户端示例

下列的 GreetingClient 是一个利用一个套接字连接到服务器的客户端程序，它发送一个问候，并等待响应。  

```
// File Name GreetingClient.java

import java.net.*;
import java.io.*;

public class GreetingClient
{
   public static void main(String [] args)
   {
      String serverName = args[0];
      int port = Integer.parseInt(args[1]);
      try
      {
         System.out.println("Connecting to " + serverName
                             + " on port " + port);
         Socket client = new Socket(serverName, port);
         System.out.println("Just connected to "
                      + client.getRemoteSocketAddress());
         OutputStream outToServer = client.getOutputStream();
         DataOutputStream out =
                       new DataOutputStream(outToServer);

         out.writeUTF("Hello from "
                      + client.getLocalSocketAddress());
         InputStream inFromServer = client.getInputStream();
         DataInputStream in =
                        new DataInputStream(inFromServer);
         System.out.println("Server says " + in.readUTF());
         client.close();
      }catch(IOException e)
      {
         e.printStackTrace();
      }
   }
}
```

## 套接字服务器示例

下列的 GreetingServer 程序是一个使用 Socket 类来监听由命令行参数指定的端口号上的客户端的服务器应用程序的一个例子：  

```
// File Name GreetingServer.java

import java.net.*;
import java.io.*;

public class GreetingServer extends Thread
{
   private ServerSocket serverSocket;
   
   public GreetingServer(int port) throws IOException
   {
      serverSocket = new ServerSocket(port);
      serverSocket.setSoTimeout(10000);
   }

   public void run()
   {
      while(true)
      {
         try
         {
            System.out.println("Waiting for client on port " +
            serverSocket.getLocalPort() + "...");
            Socket server = serverSocket.accept();
            System.out.println("Just connected to "
                  + server.getRemoteSocketAddress());
            DataInputStream in =
                  new DataInputStream(server.getInputStream());
            System.out.println(in.readUTF());
            DataOutputStream out =
                 new DataOutputStream(server.getOutputStream());
            out.writeUTF("Thank you for connecting to "
              + server.getLocalSocketAddress() + "\nGoodbye!");
            server.close();
         }catch(SocketTimeoutException s)
         {
            System.out.println("Socket timed out!");
            break;
         }catch(IOException e)
         {
            e.printStackTrace();
            break;
         }
      }
   }
   public static void main(String [] args)
   {
      int port = Integer.parseInt(args[0]);
      try
      {
         Thread t = new GreetingServer(port);
         t.start();
      }catch(IOException e)
      {
         e.printStackTrace();
      }
   }
}
```  

编译客户端和服务器然后像这样开始服务器：
  
```
$ java GreetingServer 6066
Waiting for client on port 6066...  
```

像这样检查客户端程序：

```
$ java GreetingClient localhost 6066
Connecting to localhost on port 6066
Just connected to localhost/127.0.0.1:6066
Server says Thank you for connecting to /127.0.0.1:6066
Goodbye!
```