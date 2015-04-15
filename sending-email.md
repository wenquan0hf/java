# Java - 发送邮件
用你的 Java 应用程序来发送一封电子邮件是足够简单的但是开始时你应该在你的机器上安装有 JavaMail API 和 Java Activation Framework (JAF)。  

-你可以从 Java 的标准企业网站上下载最新的 [JavaMail（1.2 版本）](http://www.oracle.com/technetwork/java/index.html)版本。  
-你可以从 Java 的标准企业网站上下载最新的 [JAF（1.1.1 版本）](http://www.oracle.com/technetwork/java/index.html)版本。

下载并解压这些文件，在新创建的顶级目录中你将找到许多应用程序的 jar 文件。你需要在你的 CLASSPATH 中添加 mail.jar 和 activation.jar 文件。  

##发送一封简单的电子邮件
这儿是从你的机器中发送一封简单的电子邮件的例子。这里假设你的本地主机连接到了因特网并且能够发送一封电子邮件。  

```
// File Name SendEmail.java

import java.util.*;
import javax.mail.*;
import javax.mail.internet.*;
import javax.activation.*;

public class SendEmail
{
   public static void main(String [] args)
   {    
      // Recipient's email ID needs to be mentioned.
      String to = "abcd@gmail.com";

      // Sender's email ID needs to be mentioned
      String from = "web@gmail.com";

      // Assuming you are sending email from localhost
      String host = "localhost";

      // Get system properties
      Properties properties = System.getProperties();

      // Setup mail server
      properties.setProperty("mail.smtp.host", host);

      // Get the default Session object.
      Session session = Session.getDefaultInstance(properties);

      try{
         // Create a default MimeMessage object.
         MimeMessage message = new MimeMessage(session);

         // Set From: header field of the header.
         message.setFrom(new InternetAddress(from));

         // Set To: header field of the header.
         message.addRecipient(Message.RecipientType.TO,
                                  new InternetAddress(to));

         // Set Subject: header field
         message.setSubject("This is the Subject Line!");

         // Now set the actual message
         message.setText("This is actual message");

         // Send message
         Transport.send(message);
         System.out.println("Sent message successfully....");
      }catch (MessagingException mex) {
         mex.printStackTrace();
      }
   }
}
```

编译并运行这个程序来发送一封简单的电子邮件： 
``` 
$ java SendEmail
Sent message successfully....
```

如果你想要给多个收信者发送一封电子邮件，那么以下的方法将被用来发送给指定的多个电子邮件 ID：
```
void addRecipients(Message.RecipientType type, 
                   Address[] addresses)
throws MessagingException
```
这是参数的描述：  
-**type：**这将被设置为 TO，CC或者BCC。这里 CC 表示副本，BCC表示黑炭副本。Message.RecipientType.TO 为例。  
-**addresses:**这是电子邮件 ID 的数组。当指定电子邮件 ID 时，你需要使用 InternetAddress()。

## 发送一封 HTML 电子邮件
这是从你的机器发送一封 HTML 电子邮件的例子。这里假设你的本地主机连接到了因特网并且能够发送一封电子邮件。  

这个例子和前一个非常相似，除了在这儿我们用 setContent（）方法来设置第二个参数为"text/html"以指定 HTML 内容被包括在消息中的内容。  

使用这个例子，你可以你喜欢的任何大的 HTML 内容。  
```
// File Name SendHTMLEmail.java

import java.util.*;
import javax.mail.*;
import javax.mail.internet.*;
import javax.activation.*;

public class SendHTMLEmail
{
   public static void main(String [] args)
   {
      
      // Recipient's email ID needs to be mentioned.
      String to = "abcd@gmail.com";

      // Sender's email ID needs to be mentioned
      String from = "web@gmail.com";

      // Assuming you are sending email from localhost
      String host = "localhost";

      // Get system properties
      Properties properties = System.getProperties();

      // Setup mail server
      properties.setProperty("mail.smtp.host", host);

      // Get the default Session object.
      Session session = Session.getDefaultInstance(properties);

      try{
         // Create a default MimeMessage object.
         MimeMessage message = new MimeMessage(session);

         // Set From: header field of the header.
         message.setFrom(new InternetAddress(from));

         // Set To: header field of the header.
         message.addRecipient(Message.RecipientType.TO,
                                  new InternetAddress(to));

         // Set Subject: header field
         message.setSubject("This is the Subject Line!");

         // Send the actual HTML message, as big as you like
         message.setContent("<h1>This is actual message</h1>",
                            "text/html" );

         // Send message
         Transport.send(message);
         System.out.println("Sent message successfully....");
      }catch (MessagingException mex) {
         mex.printStackTrace();
      }
   }
}
```  

编译并运行这个程序来发送一封 HTML 的电子邮件：  
```
$ java SendHTMLEmail
Sent message successfully....
```

## 发送电子邮件中的附件
这儿是一个从你的机器中发送一封带有附件的电子邮件的例子。这里假设你的本地主机连接到了因特网并且能够发送一封电子邮件。  
```
// File Name SendFileEmail.java

import java.util.*;
import javax.mail.*;
import javax.mail.internet.*;
import javax.activation.*;

public class SendFileEmail
{
   public static void main(String [] args)
   {
      
      // Recipient's email ID needs to be mentioned.
      String to = "abcd@gmail.com";

      // Sender's email ID needs to be mentioned
      String from = "web@gmail.com";

      // Assuming you are sending email from localhost
      String host = "localhost";

      // Get system properties
      Properties properties = System.getProperties();

      // Setup mail server
      properties.setProperty("mail.smtp.host", host);

      // Get the default Session object.
      Session session = Session.getDefaultInstance(properties);

      try{
         // Create a default MimeMessage object.
         MimeMessage message = new MimeMessage(session);

         // Set From: header field of the header.
         message.setFrom(new InternetAddress(from));

         // Set To: header field of the header.
         message.addRecipient(Message.RecipientType.TO,
                                  new InternetAddress(to));

         // Set Subject: header field
         message.setSubject("This is the Subject Line!");

         // Create the message part 
         BodyPart messageBodyPart = new MimeBodyPart();

         // Fill the message
         messageBodyPart.setText("This is message body");
         
         // Create a multipar message
         Multipart multipart = new MimeMultipart();

         // Set text message part
         multipart.addBodyPart(messageBodyPart);

         // Part two is attachment
         messageBodyPart = new MimeBodyPart();
         String filename = "file.txt";
         DataSource source = new FileDataSource(filename);
         messageBodyPart.setDataHandler(new DataHandler(source));
         messageBodyPart.setFileName(filename);
         multipart.addBodyPart(messageBodyPart);

         // Send the complete message parts
         message.setContent(multipart );

         // Send message
         Transport.send(message);
         System.out.println("Sent message successfully....");
      }catch (MessagingException mex) {
         mex.printStackTrace();
      }
   }
}
```
编译并运行这个程序来发送一封 HTML 电子邮件：
```
$ java SendFileEmail
Sent message successfully....
```

##用户身份认证部分：
如果为了身份认证的目的需要给电子邮件服务器提供用户 ID 和密码，你可以像这样设置这些属性：  
```
 props.setProperty("mail.user", "myuser");
 props.setProperty("mail.password", "mypwd");
```

电子邮件发送机制的剩余部分和上述解释的一样。

