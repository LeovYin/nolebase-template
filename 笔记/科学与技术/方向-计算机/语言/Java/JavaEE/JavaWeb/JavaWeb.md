Java Web 是指使用 Java 技术栈开发 Web 应用程序的一系列技术和框架。Java Web 应用程序通常运行在 Java 服务器上，如 Apache Tomcat、Jetty 或 JBoss 等。学习JavaWab，我们能跨越不同的主机，进行I/O流操作。

# 计算机网络基础
## 计算机网络
在学习JavaWeb之前，我们必须了解到一些必要的`计算机网络`相关内容。
详情见[[网络工程基础]]

## Socket技术
Socket技术是一种用于实现网络通信的编程接口和技术。通过Socket技术，程序员可以在应用层直接访问传输层的功能，实现网络数据的发送和接收。Socket技术通常用于网络编程中，用于建立网络连接、传输数据和实现网络应用。

### Java中的Socket技术
通过Socket技术（它是计算机之间进行**通信**的**一种约定**或一种方式），我们就可以实现两台计算机之间的通信，Socket也被翻译为`套接字`，是操作系统底层提供的一项通信技术，它支持TCP和UDP。而Java就对socket底层支持进行了一套完整的封装，我们可以通过Java来实现Socket通信。

要实现Socket通信，我们必须创建一个数据发送者和一个数据接收者，也就是客户端和服务端，我们需要提前启动服务端，来等待客户端的连接，而客户端只需要随时启动去连接服务端即可！

```java
//服务端
public static void main(String[] args) {
    try(ServerSocket server = new ServerSocket(8080)){    //将服务端创建在端口8080上
        System.out.println("正在等待客户端连接...");
        Socket socket = server.accept();  //当没有客户端连接时，线程会阻塞，直到有客户端连接为止
        System.out.println("客户端已连接，IP地址为："+socket.getInetAddress().getHostAddress());
    }catch (IOException e){
        e.printStackTrace();
    }
}
```

```java
//客户端
public static void main(String[] args) {
    try (Socket socket = new Socket("localhost", 8080)){
        System.out.println("已连接到服务端！");
    }catch (IOException e){
        System.out.println("服务端连接失败！");
        e.printStackTrace();
    }
}
```

## 使用Socket进行数据传输
通过Socket对象，我们就可以获取到对应的I/O流进行网络数据传输：
```java
public static void main(String[] args) {
        try (Socket socket = new Socket("localhost", 8080);
             Scanner scanner = new Scanner(System.in)){
            System.out.println("已连接到服务端！");
            OutputStream stream = socket.getOutputStream();
            OutputStreamWriter writer = new OutputStreamWriter(stream);  //通过转换流来帮助我们快速写入内容
            System.out.println("请输入要发送给服务端的内容：");
            String text = scanner.nextLine();
            writer.write(text+'\n');   //因为对方是readLine()这里加个换行符
            writer.flush();
            System.out.println("数据已发送："+text);
        }catch (IOException e){
            System.out.println("服务端连接失败！");
            e.printStackTrace();
        }finally {
            System.out.println("客户端断开连接！");
        }
    }
}
```

```java
public static void main(String[] args) {
    try(ServerSocket server = new ServerSocket(8080)){    //将服务端创建在端口8080上
        System.out.println("正在等待客户端连接...");
        Socket socket = server.accept();
        System.out.println("客户端已连接，IP地址为："+socket.getInetAddress().getHostAddress());
        BufferedReader reader = new BufferedReader(new InputStreamReader(socket.getInputStream()));  //通过
        System.out.print("接收到客户端数据：");
        System.out.println(reader.readLine());
      	socket.close();   //和服务端TCP连接完成之后，记得关闭socket
    }catch (IOException e){
        e.printStackTrace();
    }
}
```

同理，既然服务端可以读取客户端的内容，客户端也可以在发送后等待服务端给予响应：

```java
public static void main(String[] args) {
    try (Socket socket = new Socket("localhost", 8080);
         Scanner scanner = new Scanner(System.in)){
        System.out.println("已连接到服务端！");
        OutputStream stream = socket.getOutputStream();
        OutputStreamWriter writer = new OutputStreamWriter(stream);  //通过转换流来帮助我们快速写入内容
        System.out.println("请输入要发送给服务端的内容：");
        String text = scanner.nextLine();
        writer.write(text+'\n');   //因为对方是readLine()这里加个换行符
        writer.flush();
        System.out.println("数据已发送："+text);
        BufferedReader reader = new BufferedReader(new InputStreamReader(socket.getInputStream()));
        System.out.println("收到服务器返回："+reader.readLine());
    }catch (IOException e){
        System.out.println("服务端连接失败！");
        e.printStackTrace();
    }finally {
        System.out.println("客户端断开连接！");
    }
}
```

```java
public static void main(String[] args) {
    try(ServerSocket server = new ServerSocket(8080)){    //将服务端创建在端口8080上
        System.out.println("正在等待客户端连接...");
        Socket socket = server.accept();
        System.out.println("客户端已连接，IP地址为："+socket.getInetAddress().getHostAddress());
        BufferedReader reader = new BufferedReader(new InputStreamReader(socket.getInputStream()));  //通过
        System.out.print("接收到客户端数据：");
        System.out.println(reader.readLine());
        OutputStreamWriter writer = new OutputStreamWriter(socket.getOutputStream());
        writer.write("已收到！");
        writer.flush();
    }catch (IOException e){
        e.printStackTrace();
    }
}
```
我们可以手动关闭单向的流：

```java
socket.shutdownOutput();  //关闭输出方向的流
socket.shutdownInput();  //关闭输入方向的流
```
如果我们不希望服务端等待太长的时间，我们可以通过调用`setSoTimeout()`方法来设定IO超时时间：
```java
socket.setSoTimeout(3000);
```
当超过设定时间都依然没有收到客户端或是服务端的数据时，会抛出异常。

我们之前使用的都是通过构造方法直接连接服务端，那么是否可以等到我们想要的时候再去连接呢？
```java
try (Socket socket = new Socket(); //调用无参构造不会自动连接
     Scanner scanner = new Scanner(System.in)){ 
    socket.connect(new InetSocketAddress("localhost", 8080), 1000);  //手动调用connect方法进行连接
```

如果连接的双方发生意外而通知不到对方，导致一方还持有连接，这样就会占用资源，因此我们可以使用`setKeepAlive()`方法来防止此类情况发生：

```java
socket.setKeepAlive(true);
```
当客户端连接后，如果设置了keeplive为 true，当对方没有发送任何数据过来，超过一个时间(看系统内核参数配置)，那么我们这边会发送一个ack探测包发到对方，探测双方的TCP/IP连接是否有效。

TCP在传输过程中，实际上会有一个缓冲区用于数据的发送和接收，此缓冲区大小为：8192，我们可以手动调整其大小来优化传输效率：
```java
socket.setReceiveBufferSize(25565);   //TCP接收缓冲区
socket.setSendBufferSize(25565);    //TCP发送缓冲区
```

## 使用Socket传输文件

既然Socket为我们提供了IO流便于数据传输，那么我们就可以轻松地实现文件传输了。

## Socket类的常见方法
1. **构造方法**：
    - `Socket()`：创建一个未连接的Socket。
    - `Socket(String host, int port)`：创建一个连接到指定主机和端口的Socket。
    - `Socket(InetAddress address, int port)`：创建一个连接到指定IP地址和端口的Socket。
2. **连接方法**：
    - `connect(SocketAddress endpoint)`：将Socket连接到指定的服务器地址。
    - `connect(SocketAddress endpoint, int timeout)`：将Socket连接到指定的服务器地址，并设置连接超时时间。
3. **输入输出流方法**：
    - `getInputStream()`：返回此Socket的输入流，用于从Socket读取数据。
    - `getOutputStream()`：返回此Socket的输出流，用于向Socket写入数据。
4. **地址和端口方法**：
    - `getInetAddress()`：返回Socket连接的服务器地址。
    - `getPort()`：返回Socket连接的服务器端口。
    - `getLocalAddress()`：返回Socket绑定的本地地址。
    - `getLocalPort()`：返回Socket绑定的本地端口。
5. **Socket选项方法**：
    - `setSoTimeout(int timeout)`：设置Socket的读取超时时间。
    - `getSoTimeout()`：获取Socket的读取超时时间。
    - `setTcpNoDelay(boolean on)`：启用或禁用TCP_NODELAY选项，影响数据包的发送时机。
    - `getTcpNoDelay()`：获取TCP_NODELAY选项的状态。
    - `setKeepAlive(boolean on)`：启用或禁用SO_KEEPALIVE选项，用于检测连接是否仍然有效。
    - `getKeepAlive()`：获取SO_KEEPALIVE选项的状态。
6. **关闭方法**：
    - `close()`：关闭Socket连接，释放相关资源。
7. **其他方法**：
    - `isConnected()`：检查Socket是否已连接。
    - `isClosed()`：检查Socket是否已关闭。
    - `isBound()`：检查Socket是否已绑定到本地地址和端口。
    - `isInputShutdown()`：检查Socket的输入流是否已关闭。
    - `isOutputShutdown()`：检查Socket的输出流是否已关闭。

## Socket类的常见方法
1. **构造方法**：
    - `ServerSocket()`：创建一个未绑定的服务器Socket。
    - `ServerSocket(int port)`：创建一个绑定到指定端口的服务器Socket。
    - `ServerSocket(int port, int backlog)`：创建一个绑定到指定端口的服务器Socket，并指定连接请求队列的最大长度。
    - `ServerSocket(int port, int backlog, InetAddress bindAddr)`：创建一个绑定到指定端口和IP地址的服务器Socket，并指定连接请求队列的最大长度。
2. **绑定方法**：
    - `bind(SocketAddress endpoint)`：将服务器Socket绑定到指定的地址和端口。
    - `bind(SocketAddress endpoint, int backlog)`：将服务器Socket绑定到指定的地址和端口，并指定连接请求队列的最大长度。
3. **监听和接受连接方法**：
    - `accept()`：监听并接受客户端的连接请求，返回一个新的Socket对象，用于与客户端进行通信。
4. **地址和端口方法**：
    - `getInetAddress()`：返回服务器Socket绑定的地址。
    - `getLocalPort()`：返回服务器Socket绑定的端口。
    - `getLocalSocketAddress()`：返回服务器Socket绑定的地址和端口。
5. **Socket选项方法**：
    - `setSoTimeout(int timeout)`：设置`accept()`方法的超时时间，如果在指定时间内没有连接请求，将抛出`SocketTimeoutException`。
    - `getSoTimeout()`：获取`accept()`方法的超时时间。
6. **关闭方法**：
    - `close()`：关闭服务器Socket，释放相关资源。
7. **其他方法**：
    - `isBound()`：检查服务器Socket是否已绑定到本地地址和端口。
    - `isClosed()`：检查服务器Socket是否已关闭。


# 数据库基础
## MySQL
MySQL是一个流行的开源关系型数据库管理系统（RDBMS），广泛用于各种规模的应用程序中。详情见[[MySQL]]
## JDBC操作库
JDBC是什么？JDBC英文名为：Java Data Base Connectivity(Java数据库连接)，官方解释它是Java编程语言和广泛的数据库之间独立于数据库的连接标准的Java API，根本上说JDBC是一种规范，它提供的接口，一套完整的，允许便捷式访问底层数据库。可以用JAVA来写不同类型的可执行文件：JAVA应用程序、JAVA Applets、Java Servlet、JSP等，不同的可执行文件都能通过JDBC访问数据库，又兼备存储的优势。简单说它就是Java与数据库的连接的桥梁或者插件，用Java代码就能操作数据库的增删改查、存储过程、事务等。

我们可以发现，JDK自带了一个`java.sql`包，而这里面就定义了大量的接口，不同类型的数据库，都可以通过实现此接口，编写适用于自己数据库的实现类。而不同的数据库厂商实现的这套标准，我们称为`数据库驱动`。

### 准备工作

那么我们首先来进行一些准备工作，以便开始JDBC的学习：

* 将IDEA或者Navicat连接到我们的数据库，以便以后调试。
* 创建一个新的用于学习的数据库。
* 将mysql驱动jar依赖导入到项目中（推荐6.0版本以上，这里用到是8.0）(之后用Maven就行)

一个Java程序并不是一个人的战斗，我们可以在别人开发的基础上继续向上开发，其他的开发者可以将自己编写的Java代码打包为`jar`，我们只需要导入这个`jar`作为依赖，即可直接使用别人的代码，就像我们直接去使用JDK提供的类一样。

### 使用JDBC连接数据库
在开始之前开头打印一下看看自己的依赖是否成功引入：
```java
public static void main(String[] args){
//DriverManager是管理数据库驱动的工具类，我们可以通过它来查看当前已经引入的驱动列表
DriverManager.drivers().forEach(System.out::println);
}
```
