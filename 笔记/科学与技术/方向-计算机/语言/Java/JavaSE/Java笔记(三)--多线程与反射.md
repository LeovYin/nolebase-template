---
tags: 
aliases: 
data: 2024-07-16
---
# 多线程
多线程（Multithreading）是指在一个程序中同时执行多个线程的机制。在 Java 中，多线程是一种非常重要的编程技术，能够充分利用计算机的多核处理器和多任务处理能力，提高程序的并发性能和响应速度。
## 线程的创建和启动
在 Java 中，可以通过继承 Thread 类或实现 Runnable 接口来创建线程，然后通过调用 start() 方法来启动线程。
1. 继承`Thread`类
	1. 普通类继承`Thread`类
	2. 实现`run( )`方法
	3. thread.start();
2. 实现`Runnable`接口
	1. 普通类加上`implements Runnable`
	2. 实现`run( )`方法
	3. Thread thread = new Thread(myRunnable);
	4. thread.start();
## 线程的休眠和中断
我们前面提到，一个线程处于运行状态下，线程的下一个状态会出现以下情况：

- 当CPU给予的运行时间结束时，会从运行状态回到就绪（可运行）状态，等待下一次获得CPU资源。
- 当线程进入休眠 / 阻塞(如等待IO请求) / 手动调用`wait()`方法时，会使得线程处于等待状态，当等待状态结束后会回到就绪状态。
- 当线程出现异常或错误 / 被`stop()` 方法强行停止 / 所有代码执行结束时，会使得线程的运行终止。

而这个部分我们着重了解一下线程的休眠和中断，首先我们来了解一下如何使得线程进如休眠状态：

### 线程的休眠（Sleep）

线程的休眠是指让当前线程暂停执行一段时间，进入阻塞状态，不占用CPU资源。休眠结束后，线程会重新进入就绪状态，等待CPU调度。

#### 使用方法

Java中可以使用`Thread.sleep`方法来实现线程的休眠。`Thread.sleep`方法有两个重载版本：

- `static void sleep(long millis)`：休眠指定的毫秒数。
- `static void sleep(long millis, int nanos)`：休眠指定的毫秒数和纳秒数。


### 线程的中断（Interrupt）

线程的中断是一种协作机制，用于通知线程应该停止当前工作并进行清理。中断并不会强制线程立即停止，而是通过设置线程的中断状态来实现。

#### 使用方法

Java中可以使用`Thread.interrupt`方法来中断一个线程。被中断的线程可以通过检查中断状态来决定是否停止执行。

- `void interrupt()`：中断线程。
- `boolean isInterrupted()`：检查线程是否被中断。
- `static boolean interrupted()`：检查当前线程是否被中断，并清除中断状态。
## 线程的优先级
实际上，Java程序中的每个线程并不是平均分配CPU时间的，为了使得线程资源分配更加合理，Java采用的是抢占式调度方式，优先级越高的线程，优先使用CPU资源！我们希望CPU花费更多的时间去处理更重要的任务，而不太重要的任务，则可以先让出一部分资源。线程的优先级一般分为以下三种：

- MIN_PRIORITY  最低优先级
- MAX_PRIORITY  最高优先级
- NOM_PRIORITY  常规优先级

## 线程的礼让和加入
在线程编程中，线程的礼让（yield）和加入（join）是两种常用的线程控制方式，用于控制线程的执行顺序和协作。

1. **线程的礼让（yield）**：
    - 线程的礼让是一种线程主动放弃 CPU 执行权的行为，让其他线程有机会执行。
    - 当一个线程调用礼让操作时，它会暂时让出 CPU 执行权，让其他处于就绪状态的线程有机会执行。
    - 线程的礼让可以帮助避免线程长时间占用 CPU 而导致其他线程无法执行的情况。
    - 在大多数编程语言的线程库中，都提供了线程的礼让机制，开发者可以在适当的时候使用。
2. **线程的加入（join）**：
    - 线程的加入是一种线程协作的机制，用于让一个线程等待另一个线程执行完毕后再继续执行。
    - 当一个线程调用另一个线程的加入操作时，它会被阻塞，直到被加入的线程执行完毕。
    - 线程的加入通常用于等待子线程执行完毕后再进行后续操作，或者确保线程执行的顺序。

## 线程锁和线程同步
在多线程编程中，线程锁（Lock）和线程同步（Synchronization）是两个重要的概念，用于确保多个线程之间的协调和共享资源的安全访问。

1. **在方法中使用 `synchronized`**：
- 通过在方法声明中使用 `synchronized` 关键字，可以确保整个方法在同一时刻只有一个线程可以访问。示例代码如下：
```java
public synchronized void synchronizedMethod() {   
// 方法体 
}
```
2. **在代码块中使用 `synchronized`**：
- 通过在代码块中使用 `synchronized` 关键字，可以指定一个对象作为锁，确保只有持有该对象锁的线程可以访问代码块内的内容。示例代码如下：
```java
Object lock = new Object(); 
synchronized(lock) {     
// 代码块
}
```
        
3. **静态方法中的 `synchronized`**：
    
- 当在静态方法上使用 `synchronized` 关键字时，该方法将锁定整个类的 Class 对象，确保在同一时刻只有一个线程可以访问该静态方法。示例代码如下：
```java
public static synchronized void synchronizedStaticMethod() {    
// 静态方法体 
}
```
        
4. **同步代码块中的对象锁**：
- 在使用同步代码块时，需要指定一个对象作为锁。多个同步代码块可以使用同一个对象作为锁，以确保线程之间的同步。示例代码如下：
```java
Object lock = new Object(); 
synchronized(lock) {    
// 代码块1
} 
// 其他代码 
synchronized(lock) {    
// 代码块2
}
```
## 死锁
在Java多线程编程中，死锁（Deadlock）是一种常见的并发问题，指的是两个或多个线程互相持有对方所需的资源，并且在等待对方释放资源时陷入了永久等待的状态。这种情况会导致所有线程都无法继续执行，造成程序无响应或僵死的状态。

以下是导致死锁的常见情形：

1. **互斥条件**：线程持有一个资源，并且在等待另一个资源时不释放已持有的资源。
2. **请求和保持条件**：线程持有一个资源，并且在请求另一个资源时保持原有资源不释放。
3. **循环等待条件**：多个线程形成循环等待资源的关系，每个线程都在等待另一个线程释放资源。

为了避免死锁，可以采取以下措施：

1. **避免嵌套锁**：尽量减少代码中的嵌套锁，避免同时持有多个锁。
2. **按固定的顺序获取锁**：确保线程获取锁的顺序是一致的，避免循环等待的情况。
3. **设置超时时间**：在获取锁时设置超时时间，避免长时间等待锁资源。
4. **使用并发工具类**：Java提供了一些并发工具类如 `ReentrantLock`，可以更灵活地控制锁的获取和释放。
5. `jstack`命令来检测死锁
6. 利用`jconsole`来检测死锁

因此，前面说不推荐使用 `suspend()`去挂起线程的原因，是因为`suspend()`在使线程暂停的同时，并不会去释放任何锁资源。其他线程都无法访问被它占用的锁。直到对应的线程执行`resume()`方法后，被挂起的线程才能继续，从而其它被阻塞在这个锁的线程才可以继续执行。但是，如果`resume()`操作出现在`suspend()`之前执行，那么线程将一直处于挂起状态，同时一直占用锁，这就产生了死锁。
## wait和notify方法
在Java中，`wait()` 和 `notify()` 方法是用于实现线程之间协作的机制，通常与`synchronized`关键字一起使用。这两个方法通常用于实现生产者-消费者模式或者线程间通信。

1. `wait()` 方法：
    
    - `wait()` 方法是`Object`类中定义的方法，用于将当前线程置于等待状态，并释放对象的锁。
    - 当一个线程调用`wait()`方法时，它会释放当前持有的对象锁，并等待其他线程调用相同对象的`notify()` 或 `notifyAll()` 方法来唤醒它。
    - 线程在调用`wait()`方法后会进入对象的等待队列，直到被其他线程唤醒或等待时间到达。
2. `notify()` 方法：
    
    - `notify()` 方法也是`Object`类中定义的方法，用于唤醒在对象等待队列中等待的一个线程（随机选择）。
    - 如果有多个线程在等待同一个对象的锁，调用`notify()`方法只会唤醒其中的一个线程；如果希望唤醒所有等待线程，可以使用`notifyAll()` 方法。

## ThreadLocal的使用
 `ThreadLocal` 是 Java 中的一个类，用于实现线程局部变量。每个线程都可以通过 `ThreadLocal` 创建自己的局部变量，这样每个线程可以独立地访问自己的局部变量，互不干扰。

下面是 `ThreadLocal` 的基本用法：
1. `ThreadLocal<String> threadLocal = new ThreadLocal<>();`：创建 `ThreadLocal` 对象

2. `threadLocal.set("Value");`：设置当前线程的局部变量的值

3. `String value = threadLocal.get();`：获取当前线程的局部变量的值

4. `threadLocal.remove();`：移除当前线程的局部变量

## 定时器
`Timer` 类是 Java 中用于执行定时任务的工具类，它允许你在指定的时间间隔内执行某个任务。`Timer` 类是线程安全的，可以用于在后台线程中执行定时任务。

下面是 `Timer` 类的基本用法：

1. 创建 `Timer` 对象：
```java
Timer timer = new Timer();
```
2. 定义一个继承自 `TimerTask` 的任务类，重写 `run()` 方法，定义具体的任务逻辑：
```java
class MyTask extends TimerTask {     @Override     public void run() {         // 任务逻辑         
System.out.println("Task is running...");     
} 
}
```
3. 使用 `Timer` 对象调度任务：

```java
timer.schedule(new MyTask(), delay, period);
```
其中，`delay` 表示延迟多久后开始执行任务（单位为毫秒），`period` 表示任务执行的时间间隔（单位为毫秒）。
4. 取消任务：

```java
timer.cancel();
```


## 守护线程
在 Java 中，线程可以分为守护线程（Daemon Thread）和用户线程（User Thread）。守护线程是一种在后台提供服务的线程，当所有的用户线程结束时，守护线程会自动销毁。守护线程通常被用来执行一些后台任务，如垃圾回收、内存管理等。
在 Java 中，通过设置线程的 `setDaemon(true)` 方法可以将线程设置为守护线程。守护线程需要在启动线程之前设置。

```java
Thread daemonThread = new Thread(() -> {     // 守护线程的任务逻辑 }); 
daemonThread.setDaemon(true); 
// 设置为守护线程 
daemonThread.start(); 
// 启动线程
```
# 反射
反射（Reflection）是指在运行时检查或修改类、方法、属性等程序结构的能力。在 Java 中，反射机制允许程序在运行时获取类的信息、调用类的方法、访问类的属性等，而无需在编译时确定这些信息。
## Class类详解
在 Java 中，可以通过以下几种方式获取 Class 类对象：

1. **使用类的.class属性**：  
    每个类在 JVM 中都有一个对应的 Class 对象，可以通过类的 `.class` 属性来获取该类的 Class 对象。
    ```java
    Class<?> clazz = MyClass.class;
```
    
2. **调用对象的getClass()方法**：  
    可以通过对象的 `getClass()` 方法来获取该对象所属类的 Class 对象。
    
    ```java
    MyClass obj = new MyClass(); Class<?> clazz = obj.getClass();
    ```
    
3. **使用Class.forName()方法**：  
    可以通过 Class 类的静态方法 `forName()` 来根据类的全限定名（包括包名）获取该类的 Class 对象。
    
    ```java
    Class<?> clazz = Class.forName("com.example.MyClass");
    ```
    
4. **使用ClassLoader的loadClass()方法**：  
    可以通过 ClassLoader 的 `loadClass()` 方法来加载类，并获取该类的 Class 对象。
    
    ```java
    ClassLoader classLoader = MyClass.class.getClassLoader(); Class<?> clazz = classLoader.loadClass("com.example.MyClass
    ```

## Class对象与多态

## 创建类对象

## 调用类方法

## 修改类的属性

## 类加载器

# 注解

## 预设注解

## 元注解

## 注解的使用

## 反射获取注解

