# Java 环境设置 
 
## 本地环境设置

如果你依然想要为 Java 编程语言设置环境，那么本节将指导你如何在你的电脑上下载和设置 Java。请按照以下步骤进行环境设置。 
 
Java SE 可以从下载 Java 这个链接免费下载。你可以根据你的系统类型下载相应版本的 Java。  

按照上述指导下载 Java 然后运行 .exe 文件进行安装。你在电脑上安装完 Java 之后，你需要将环境变量设置到指定目录。  

## Windows XP/7/8 系统下的设置方法

假设你把 Java 安装在 `c:\Program Files\java\jdk` 路径下：  

- 右键点击「我的电脑」选择「属性」选项  
- 在高级标签下点击「环境变量」按钮  
- 现在，改变变量的路径使其包含可执行的 Java 程序。  
例如：如果现在的路径设置的是   
`C:\WINDOWS\SYSTEM32`，  
那么就要将其改成
`C:\WINDOWS\SYSTEM32;c:\ProgramFiles\java\jdk\bin`。  

## Linux, UNIX, Solaris, FreeBSD 系统下的设置方法
 
环境变量路径必须指向 Java 文件的安装位置。如果进行该设置时有任何问题，请参考shell帮助文档。 
 
例如，如果你用 bash 作为你的 shell ，那么在你的 shell 最后加入如下代码    
`.bashrc: export PATH=/path/to/java:$PATH`

## 流行的 Java 编辑器
 
在编写 Java 程序时，你需要一个文本编辑器。市场中有很多精致的编辑器。但是就现在而言，你可以考虑下面几个：  

- **记事本**：在 Windows 计算机中你可以使用像记事本（本指导推荐），日记本这样的简单的文本编辑器。  
- **Netbeans**：这是一款开源且免费的 Java 编辑器。你可以从以下链接下载 <http://www.netbeans.org/index.html>  
- **Eclipse**：这是一款由 eclipse 开源社区开发的 Java 编辑器。你可以从以下链接下载 <http://www.eclipse.org/>  

## 接下来是什么呢？
  
下一章我们将教你如何编写并且运行你的第一个程序和一些开发应用程序所必备的重要语法。  
