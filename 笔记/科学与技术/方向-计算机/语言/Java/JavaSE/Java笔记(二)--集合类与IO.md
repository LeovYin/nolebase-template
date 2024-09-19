---
tags: 
aliases:
  - Java2
data:
---
# 集合类
集合类是Java中非常重要的存在，使用频率极高。集合其实与我们数学中的集合是差不多的概念，集合表示一组对象，每一个对象我们都可以称其为元素。不同的集合有着不同的性质，比如一些集合允许重复的元素，而另一些则不允许，一些集合是有序的，而其他则是无序的。


集合类其实就是为了更好地组织、管理和操作我们的数据而存在的，包括列表、集合、队列、映射等数据结构。从这一块开始，我们会从源码角度给大家讲解（先从接口定义对于集合需要实现哪些功能开始说起，包括这些集合类的底层机制是如何运作的）不仅仅是教会大家如何去使用。

集合跟数组一样，可以表示同样的一组元素，但是他们的相同和不同之处在于：

1. 它们都是容器，都能够容纳一组元素。

不同之处：

1. 数组的大小是固定的，集合的大小是可变的。
2. 数组可以存放基本数据类型，但集合只能存放对象。
3. 数组存放的类型只能是一种，但集合可以有不同种类的元素。

## 集合根接口
在Java中，集合框架的根接口是`Collection`接口。`Collection`接口是所有集合类的父接口，定义了集合类的基本行为和操作。`Collection`接口位于`java.util`包中，它是一个泛型接口，声明了一组操作集合元素的方法。

`Collection`接口中定义了一些常用的方法，例如：

- `boolean add(E e)`：向集合中添加一个元素。
- `boolean remove(Object o)`：从集合中移除指定元素。
- `boolean contains(Object o)`：判断集合中是否包含指定元素。
- `int size()`：返回集合中元素的数量。
- `boolean isEmpty()`：判断集合是否为空。
- `void clear()`：清空集合中的所有元素。
- `Iterator<E> iterator()`：返回一个迭代器，用于遍历集合中的元素。
## List列表
首先我们需要介绍的是List列表（线性表），线性表支持随机访问，相比之前的Collection接口定义，功能还会更多一些。首先介绍ArrayList，我们已经知道，它的底层是用数组实现的，内部维护的是一个可动态进行扩容的数组，也就是我们之前所说的顺序表，跟我们之前自己写的ArrayList相比，它更加的规范，并且功能更加强大，同时实现自List接口。


Java中的List接口是有序集合，允许存储重复元素。List接口继承自Collection接口，因此包含了Collection接口中定义的方法，同时还添加了一些针对有序集合的特定方法。以下是List列表的常见属性和方法：
-  常见方法：
	1. **添加元素**：
	    - `boolean add(E e)`：向列表尾部添加元素。
	    - `void add(int index, E element)`：在指定位置插入元素。
	 2. **获取元素**：
	    - `E get(int index)`：获取指定位置的元素。
	    - `int indexOf(Object o)`：返回指定元素第一次出现的索引。
	    - `int lastIndexOf(Object o)`：返回指定元素最后一次出现的索引。
	3. **替换元素**：
	    - `E set(int index, E element)`：替换指定位置的元素。
	4. **删除元素**：
	    - `E remove(int index)`：移除指定位置的元素。
	    - `boolean remove(Object o)`：移除指定元素。
	5. **子列表**：
	    - `List<E> subList(int fromIndex, int toIndex)`：返回列表中指定范围的子列表。
	6. **判断方法**：
	    - `boolean contains(Object o)`：判断列表是否包含指定元素。
	    - `boolean isEmpty()`：判断列表是否为空。
	    - `int size()`：返回列表的大小。
	7. **迭代器**：
	    - `Iterator<E> iterator()`：返回迭代器，用于遍历列表中的元素。
	8. **其他方法**：
	    - `void clear()`：清空列表中的所有元素。
	    - `void sort(Comparator<? super E> c)`：根据指定比较器对列表进行排序。
	    - `void forEach(Consumer<? super E> action)`：对列表中的每个元素执行指定操作。
以上是List接口中一些常见的属性和方法，通过这些方法可以方便地对列表中的元素进行操作和管理。在实际开发中，根据具体的需求选择合适的List实现类（如ArrayList、LinkedList等）来存储和操作数据。

### LinkedList（链表）
#### 常见属性：
1. **size**：链表中元素的数量。
#### 常见方法：
1. `void addFirst(E e)`：在链表的头部添加元素。
2. `void addLast(E e)`：在链表的尾部添加元素。
3. `E removeFirst()`：移除并返回链表的头部元素。
4. `E removeLast()`：移除并返回链表的尾部元素。
5. `E getFirst()`：返回链表的头部元素，但不移除。
6. `E getLast()`：返回链表的尾部元素，但不移除。
## 迭代器
在Java中，List接口提供了用于遍历列表元素的迭代器。通过迭代器，可以按顺序访问列表中的每个元素，进行遍历操作。List接口继承自Collection接口，因此可以使用Collection接口中定义的iterator()方法来获取迭代器。

List的迭代器主要有两种：普通迭代器和列表迭代器。

### 1. 普通迭代器（Iterator）

普通迭代器是最基本的迭代器类型，可以用于遍历List中的元素。常见的方法有：

- `boolean hasNext()`：判断是否还有下一个元素。
- `E next()`：返回下一个元素。
- `void remove()`：移除迭代器当前位置的元素。

示例代码：


```java
List<String> list = new ArrayList<>();
list.add("Apple"); 
list.add("Banana"); 
list.add("Orange");
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {    
String element = iterator.next();    
System.out.println(element); }
```
### 2. 列表迭代器（ListIterator）

列表迭代器是普通迭代器的扩展，提供了双向遍历列表的功能。除了普通迭代器的方法外，列表迭代器还具有以下方法：

- `boolean hasPrevious()`：判断是否有前一个元素。
- `E previous()`：返回前一个元素。
- `int nextIndex()`：返回下一个元素的索引。
- `int previousIndex()`：返回前一个元素的索引。
- `void add(E e)`：在当前位置添加元素。
- `void set(E e)`：替换当前位置的元素。

示例代码：

```java
List<String> list = new ArrayList<>();
list.add("Apple");
list.add("Banana");
list.add("Orange");
ListIterator<String> listIterator = list.listIterator();
while (listIterator.hasNext()) {     
String element = listIterator.next();    
System.out.println(element); 
} 
// 反向遍历 
while (listIterator.hasPrevious()) {   
String element = listIterator.previous();     
System.out.println(element); 
}
```

通过迭代器，可以方便地遍历List中的元素，进行读取、删除、添加等操作。根据具体需求选择普通迭代器或列表迭代器来实现遍历功能。

## Queue和Deque
Queue和Deque是两种常用的接口，它们都继承自Collection接口，实现了数据结构中的队列，并提供了不同的元素操作方式。下面简要介绍一下它们的特点和区别：
### Queue（队列）

Queue是一种先进先出（FIFO）的数据结构，类似于现实生活中的排队。Queue接口继承自Collection接口，提供了一系列用于操作队列的方法。常见的实现类有LinkedList和PriorityQueue。

### PriorityQueue（优先队列）
#### 常见属性：
1. **size**：优先队列中元素的数量。
#### 常见方法：
1. `boolean add(E e)`：将元素添加到优先队列中。
2. `E remove()`：移除并返回队列中的最小元素。
3. `E poll()`：移除并返回队列中的最小元素，如果队列为空返回null。
4. `E peek()`：返回队列中的最小元素，但不移除，如果队列为空返回null。
5. `boolean offer(E e);`同样是添加操作，但是插入失败不会抛出异常 
### 区别
- **LinkedList** 是基于链表实现的，可以当作队列、栈或双端队列来使用，支持在头部和尾部进行元素的插入和删除操作。
- **PriorityQueue** 是基于优先级堆实现的，是一种优先队列，元素按照优先级顺序进行存储和访问，具有最小堆或最大堆的特性。
以上是LinkedList和PriorityQueue的常见属性和方法，通过这些方法可以对链表和优先队列进行元素的插入、删除和访问操作。在实际应用中，根据具体需求选择合适的数据结构来存储和操作数据。
### Deque（双端队列）

### ArrayDeque
ArrayDeque是Java中的一个双端队列实现类，底层基于数组实现，可以在队列的两端进行高效的插入和删除操作。下面是ArrayDeque的常见属性和方法：
#### 常见属性：
1. **size**：双端队列中元素的数量。
2. **isEmpty**：判断双端队列是否为空。
#### 常见方法：
1. `void addFirst(E e)`：在双端队列的头部添加元素。
2. `void addLast(E e)`：在双端队列的尾部添加元素。
3. `E removeFirst()`：移除并返回双端队列的头部元素。
4. `E removeLast()`：移除并返回双端队列的尾部元素。
5. `E getFirst()`：返回双端队列的头部元素，但不移除。
6. `E getLast()`：返回双端队列的尾部元素，但不移除。
7. `boolean offerFirst(E e)`：在双端队列的头部添加元素，如果队列已满则返回false。
8. `boolean offerLast(E e)`：在双端队列的尾部添加元素，如果队列已满则返回false。
9. `E pollFirst()`：移除并返回双端队列的头部元素，如果队列为空返回null。
10. `E pollLast()`：移除并返回双端队列的尾部元素，如果队列为空返回null。
11. `E peekFirst()`：返回双端队列的头部元素，但不移除，如果队列为空返回null。
12. `E peekLast()`：返回双端队列的尾部元素，但不移除，如果队列为空返回null。
#### 注意：
- ArrayDeque不是线程安全的，如果需要在多线程环境下使用，可以考虑使用`ConcurrentLinkedDeque`或`LinkedBlockingDeque`。
- ArrayDeque的底层实现是一个循环数组，当数组容量不足时会进行扩容操作，因此在频繁进行大量元素插入和删除操作时，可能会导致数组扩容带来的性能损耗。
通过上述常见属性和方法，可以方便地在ArrayDeque中进行双端队列的操作，包括元素的插入、删除和访问等操作。在实际应用中，可以根据具体需求选择合适的数据结构来管理数据。

### 区别

1. **操作方式**：Queue是单向队列，只能在队列的一端进行插入和删除操作；而Deque是双向队列，可以在队列的两端进行插入和删除操作。
2. **元素访问**：Queue通常只能访问队列头部的元素，而Deque可以访问队列的头部和尾部元素。
3. **实现类**：Queue和Deque接口都有多种实现类，可以根据具体需求选择合适的实现类来操作队列或双端队列。
## Set集合
在Java中，Set是一种集合接口，它代表着一组不重复元素的集合。Set集合不允许包含重复的元素，每个元素在Set中都是唯一的。常见的Set接口的实现类有HashSet、TreeSet和LinkedHashSet。下面是Set集合的主要特点和常见方法：

### Set集合的特点：

1. **不允许重复元素**：Set集合中的元素是唯一的，不会包含重复元素。
2. **无序性**：Set集合中的元素没有特定的顺序，不保证元素的插入顺序和访问顺序一致。
3. **基于哈希表或红黑树实现**：不同的Set实现类可能基于不同的数据结构实现，例如HashSet基于哈希表，TreeSet基于红黑树。

### Set集合常见方法：

1. `boolean add(E e)`：向Set中添加元素，如果元素已经存在返回false。
2. `boolean remove(Object o)`：从Set中移除指定元素。
3. `boolean contains(Object o)`：判断Set中是否包含指定元素。
4. `int size()`：返回Set中元素的数量。
5. `boolean isEmpty()`：判断Set是否为空。
6. `void clear()`：清空Set中的所有元素。
7. `Iterator<E> iterator()`：返回一个迭代器，用于遍历Set中的元素。
8. `void forEach(Consumer<? super E> action)`：对Set中的每个元素执行指定操作。
9. `Set<E> union(Set<? extends E> set)`：返回当前Set与另一个Set的并集。
10. `Set<E> intersection(Set<? extends E> set)`：返回当前Set与另一个Set的交集。
11. `Set<E> difference(Set<? extends E> set)`：返回当前Set与另一个Set的差集。

### Set集合的常见实现类：

1. **HashSet**：基于哈希表实现，插入、删除和查找操作的时间复杂度为O(1)，不保证元素的顺序。
2. **TreeSet**：基于红黑树实现，元素按照自然顺序或指定比较器排序，插入、删除和查找操作的时间复杂度为O(log n)。
3. **LinkedHashSet**：继承自HashSet，内部使用链表维护插入顺序，保留元素插入的顺序。

通过使用Set集合，可以方便地存储一组不重复的元素，并进行集合运算等操作。在选择Set的实现类时，可以根据具体的需求和性能要求来选择合适的实现类。


## Map集合
Map集合是Java中用于存储键值对的集合，它提供了一种通过键快速查找值的机制。在Java中，Map是一个接口，常用的实现类包括HashMap、TreeMap、LinkedHashMap等。下面是Map集合的一些常用属性和方法：

### 常用属性：

1. **size**：Map中键值对的数量。
2. **keySet**：返回包含Map中所有键的Set集合。
3. **values**：返回包含Map中所有值的Collection集合。
4. **entrySet**：返回包含Map中所有键值对（Entry）的Set集合。

### 常用方法：

1. `V get(Object key)`：根据键获取对应的值。
2. `V put(K key, V value)`：向Map中添加键值对。
3. `boolean containsKey(Object key)`：判断Map中是否包含指定的键。
4. `boolean containsValue(Object value)`：判断Map中是否包含指定的值。
5. `V remove(Object key)`：根据键移除对应的键值对。
6. `void clear()`：清空Map中的所有键值对。
7. `Set<K> keySet()`：返回包含所有键的Set集合。
8. `Collection<V> values()`：返回包含所有值的Collection集合。
9. `Set<Map.Entry<K, V>> entrySet()`：返回包含所有键值对的Set集合。
10. `boolean isEmpty()`：判断Map是否为空。
11. `void putAll(Map<? extends K, ? extends V> m)`：将另一个Map中的所有键值对添加到当前Map中。
12. `boolean equals(Object o)`：判断当前Map是否与另一个对象相等。
13. `int hashCode()`：返回Map的哈希码值。

### 注意：

- Map集合中的键是唯一的，同一个键对应的值可以重复。
- 不同的Map实现类有不同的特性，如HashMap具有快速的查找性能，而TreeMap可以按照键的自然顺序或自定义比较器进行排序。
- Map集合常用于需要通过键快速查找值的场景，如存储配置信息、缓存数据等。

通过使用Map集合，可以方便地存储和管理键值对数据，提高数据的查找效率。在Java开发中，Map集合是一个非常常用的数据结构。

## Stream流
ava 8 API添加了一个新的抽象称为流Stream，可以让你以一种声明的方式处理数据。Stream 使用一种类似用 SQL 语句从数据库查询数据的直观方式来提供一种对 Java 集合运算和表达的高阶抽象。Stream API可以极大提高Java程序员的生产力，让程序员写出高效率、干净、简洁的代码。这种风格将要处理的元素集合看作一种流， 流在管道中传输， 并且可以在管道的节点上进行处理， 比如筛选， 排序，聚合等。元素流在管道中经过中间操作（intermediate operation）的处理，最后由最终操作(terminal operation)得到前面处理的结果。

![image-20221003232832897](https://s2.loli.net/2022/10/03/r4AtmVRZ51y7uxd.png)

它看起来就像一个工厂的流水线一样！我们就可以把一个Stream当做流水线处理：

```java
public static void main(String[] args) {
    List<String> list = new ArrayList<>();
    list.add("A");
    list.add("B");
    list.add("C");
  
  	//移除为B的元素
  	Iterator<String> iterator = list.iterator();
    while (iterator.hasNext()){
        if(iterator.next().equals("B")) iterator.remove();
    }
  
  	//Stream操作
    list = list     //链式调用
            .stream()    //获取流
            .filter(e -> !e.equals("B"))   //只允许所有不是B的元素通过流水线
            .collect(Collectors.toList());   //将流水线中的元素重新收集起来，变回List
    System.out.println(list);
}
```
stream会先记录每一步操作，而不是直接开始执行内容，当整个链式调用完成后，才会依次进行，也就是说需要的时候，工厂的机器才会按照预定的流程启动。

接下来，我们用一堆随机数来进行更多流操作的演示：

```java
public static void main(String[] args) {
    Random random = new Random();  //没想到吧，Random支持直接生成随机数的流
    random
            .ints(-100, 100)   //生成-100~100之间的，随机int型数字（本质上是一个IntStream）
            .limit(10)   //只获取前10个数字（这是一个无限制的流，如果不加以限制，将会无限进行下去！）
            .filter(i -> i < 0)   //只保留小于0的数字
            .sorted()    //默认从小到大排序
            .forEach(System.out::println);   //依次打印
}
```

我们可以生成一个统计实例来帮助我们快速进行统计：

```java
public static void main(String[] args) {
    Random random = new Random();  //Random是一个随机数工具类
    IntSummaryStatistics statistics = random
            .ints(0, 100)
            .limit(100)
            .summaryStatistics();    //获取语法统计实例
    System.out.println(statistics.getMax());  //快速获取最大值
    System.out.println(statistics.getCount());  //获取数量
    System.out.println(statistics.getAverage());   //获取平均值
}
```

普通的List只需要一个方法就可以直接转换到方便好用的IntStream了：

```java
public static void main(String[] args) {
    List<Integer> list = new ArrayList<>();
    list.add(1);
    list.add(1);
    list.add(2);
    list.add(3);
    list.add(4);
    list.stream()
            .mapToInt(i -> i)    //将每一个元素映射为Integer类型（这里因为本来就是Integer）
            .summaryStatistics();
}
```

我们还可以通过`flat`来对整个流进行进一步细分：

```java
public static void main(String[] args) {
    List<String> list = new ArrayList<>();
    list.add("A,B");
    list.add("C,D");
    list.add("E,F");   //我们想让每一个元素通过,进行分割，变成独立的6个元素
    list = list
            .stream()    //生成流
            .flatMap(e -> Arrays.stream(e.split(",")))    //分割字符串并生成新的流
            .collect(Collectors.toList());   //汇成新的List
    System.out.println(list);   //得到结果
}
```

我们也可以只通过Stream来完成所有数字的和，使用`reduce`方法：

```java
public static void main(String[] args) {
    List<Integer> list = new ArrayList<>();
    list.add(1);
    list.add(2);
    list.add(3);
    int sum = list
            .stream()
            .reduce((a, b) -> a + b)   //计算规则为：a是上一次计算的值，b是当前要计算的参数，这里是求和
            .get();    //我们发现得到的是一个Optional类实例，通过get方法返回得到的值
    System.out.println(sum);
}
```

可能，作为新手来说，一次性无法接受这么多内容，但是在各位以后的开发中，就会慢慢使用到这些东西了。

## Collections工具类
Java中的Collections工具类提供了一系列静态方法，用于对集合进行常见操作，如排序、查找、替换等。这些方法可以方便地对集合进行操作，提高开发效率。下面是一些Collections工具类中常用的方法：

### 排序和查找：

1. `**sort(List\< T> list)**`：对List集合进行排序。
2. `**reverse(List\<T> list)**`：反转List集合中元素的顺序。
3. `**shuffle(List\<T> list)**`：随机打乱List集合中元素的顺序。
4. `**binarySearch(List \< ? extends Comparable \< ? super T>> list, T key)**`：对已排序的List集合进行二分查找。
5. **`max(Collection\< ? extends T> coll)**`：返回Collection中的最大元素。
6. `**min(Collection\< ? extends T> coll)**`：返回Collection中的最小元素。

### 替换和填充：

1. `**replaceAll(List\<T> list, UnaryOperator\<T> operator)**`：使用指定的操作符替换List中的所有元素。
2. `**fill(List\< ? super T> list, T obj)**`：用指定元素填充List中的所有元素。

### 同步控制：

1. **synchronizedCollection(Collection\<T> c)**：返回一个同步（线程安全）的集合。
2. **synchronizedList(List\<T> list)**：返回一个同步的List。
3. **synchronizedMap(Map\<K,V> m)**：返回一个同步的Map。
4. **unmodifiableCollection(Collection\\< ? extends T> c)**：返回一个不可修改的集合。
5. **unmodifiableList(List\< ? extends T> list)**：返回一个不可修改的List。
6. **unmodifiableMap(Map\< ? extends K,? extends V> m)**：返回一个不可修改的Map。

### 其他：

1. `**frequency(Collection\< ?> c, Object o)**`：返回指定元素在集合中出现的次数。
2. `**disjoint(Collection\< ?> c1, Collection\< ?> c2)**`：判断两个集合是否有交集。
3. **reverseOrder()**：返回一个比较器，用于逆序比较。
4. **singleton(T o)**：返回一个只包含指定元素的不可修改的Set。

这些方法能够帮助开发者更方便地对集合进行操作，提高代码的可读性和效率。Collections工具类提供了丰富的方法，可以满足不同场景下对集合的处理需求。
# IO
I/O简而言之，就是输入输出，那么为什么会有I/O呢？其实I/O无时无刻都在我们的身边，比如读取硬盘上的文件，网络文件传输，鼠标键盘输入，也可以是接受单片机发回的数据，而能够支持这些操作的设备就是I/O设备。

我们可以大致看一下整个计算机的总线结构：

![image-20221004002405375](https://s2.loli.net/2022/10/04/Q8JGeMprkgHsnPY.png)

常见的I/O设备一般是鼠标、键盘这类通过USB进行传输的外设或者是通过Sata接口或是M.2连接的硬盘。一般情况下，这些设备是由CPU发出指令通过南桥芯片间接进行控制，而不是由CPU直接操作。

而我们在程序中，想要读取这些外部连接的I/O设备中的内容，就需要将数据传输到内存中。而需要实现这样的操作，单单凭借一个小的程序是无法做到的，而操作系统（如：Windows/Linux/MacOS）就是专门用于控制和管理计算机硬件和软件资源的软件，我们需要读取一个IO设备的内容时，就可以向操作系统发出请求，由操作系统帮助我们来和底层的硬件交互以完成我们的读取/写入请求。

从读取硬盘文件的角度来说，不同的操作系统有着不同的文件系统（也就是文件在硬盘中的存储排列方式，如Windows就是NTFS、MacOS就是APFS），硬盘只能存储一个个0和1这样的二进制数据，至于0和1如何排列，各自又代表什么意思，就是由操作系统的文件系统来决定的。从网络通信角度来说，网络信号通过网卡等设备翻译为二进制信号，再交给系统进行读取，最后再由操作系统来给到程序。

（传统的SATA硬盘就是通过SATA线与电脑主板相连，这样才可以读取到数据）

JDK提供了一套用于IO操作的框架，为了方便我们开发者使用，就定义了一个像水流一样，根据流的传输方向和读取单位，分为字节流InputStream和OutputStream以及字符流Reader和Writer的IO框架，当然，这里的Stream并不是前面集合框架认识的Stream，这里的流指的是数据流，通过流，我们就可以一直从流中读取数据，直到读取到尽头，或是不断向其中写入数据，直到我们写入完成，而这类IO就是我们所说的BIO，

字节流一次读取一个字节，也就是一个`byte`的大小，而字符流顾名思义，就是一次读取一个字符，也就是一个`char`的大小（在读取纯文本文件的时候更加适合），有关这两种流，会在后面详细介绍，这个章节我们需要学习16个关键的流。
## 文件字节流
要学习和使用IO，首先就要从最易于理解的读取文件开始说起。

首先介绍一下FileInputStream，我们可以通过它来获取文件的输入流：
```java
public static void main(String[] args) {
    FileInputStream inputStream = null;    //定义可以先放在try外部
    try {//注意，IO相关操作会有很多影响因素，有可能出现异常，所以需要明确进行处理
        inputStream = new FileInputStream("路径");//路径支持相对路径和绝对路径
    } catch (FileNotFoundException e) {
        e.printStackTrace();
    } finally {//在使用完成一个流之后，必须关闭这个流来完成对资源的释放，否则资源会被一直占用：
        try {    //建议在finally中进行，因为关闭流是任何情况都必须要执行的！
            if(inputStream != null) inputStream.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
`相对路径是在当前运行目录（就是你在哪个目录运行java命令启动Java程序的）的路径下寻找文件，而绝对路径，是从根目录开始寻找。`

虽然这样的写法才是最保险的，但是显得过于繁琐了，尤其是finally中再次嵌套了一个try-catch块，因此在JDK1.7新增了try-with-resource语法，用于简化这样的写法（本质上还是和这样的操作一致，只是换了个写法）
```java
public static void main(String[] args) {

    //注意，这种语法只支持实现了AutoCloseable接口的类！
    try(FileInputStream inputStream = new FileInputStream("路径")) {   //直接在try()中定义要在完成之后释放的资源

    } catch (IOException e) {   //这里变成IOException是因为调用close()可能会出现，而FileNotFoundException是继承自IOException的
        e.printStackTrace();
    }
    //无需再编写finally语句块，因为在最后自动帮我们调用了close()
}
```
- 文件字节流的常用方法：
	- FileInputStream常见方法：
		1. **int read()**：从输入流中读取数据的下一个字节。返回所读取的字节数据，如果已到达流的末尾，则返回-1。
		2. **int read(byte[] b)**：从输入流中最多读取b.length个字节的数据到字节数组b中。返回实际读取的字节数，如果已到达流的末尾，则返回-1。
		3. **int read(byte[] b, int off, int len)**：从输入流中最多读取len个字节的数据到字节数组b中，偏移量为off。返回实际读取的字节数，如果已到达流的末尾，则返回-1。
		4. **long skip(long n)**：跳过n个字节不读取，返回实际跳过的字节数。
		5. **int available()**：返回可读的剩余字节数量（注意：并不一定真实的数据量就是这么多，尤其是在网络I/O操作时，这个方法只能进行一个预估也可以说是暂时能一次性可以读取的数量，当然在磁盘IO下，一般情况都是真实的数据量）。
		6. **void close()**：关闭输入流。
	-  FileOutputStream常见方法：
		1. **void write(int b)**：将指定的字节写入输出流。
		2. **void write(byte[] b)**：将b.length个字节从指定的字节数组写入输出流。
		3. **void write(byte[] b, int off, int len)**：将len个字节从指定的字节数组写入输出流，偏移量为off。
		4. **void flush()**：刷新输出流，将缓冲区的数据写入目标设备。
		5. **void close()**：关闭输出流。
### 文件字节流读取文件的常见格式：
```java
public static void main(String[] args) {
    try(FileOutputStream outputStream = new FileOutputStream("output.txt");
        FileInputStream inputStream = new FileInputStream("test.txt")) {   //可以写入多个
        byte[] bytes = new byte[10];    //使用长度为10的byte[]做传输媒介
        int tmp;   //存储本地读取字节数
        while ((tmp = inputStream.read(bytes)) != -1){   //直到读取完成为止
            outputStream.write(bytes, 0, tmp);    //写入对应长度的数据到输出流
        }
    }catch (IOException e){
        e.printStackTrace();
    }
}
```
## 文件字符流
字符流不同于字节，字符流是以一个具体的字符进行读取，因此它只适合读纯文本的文件，如果是其他类型的文件不适用：
```java
public static void main(String[] args) {
    try(FileReader reader = new FileReader("test.txt")){
      	reader.skip(1);   //现在跳过的是一个字符
        System.out.println((char) reader.read());   //现在是按字符进行读取，而不是字节，因此可以直接读取到中文字符
    }catch (IOException e){
        e.printStackTrace();
    }
}
```
文件字符流是Java中用于处理字符数据的流，常见的文件字符流有FileReader和FileWriter。以下是它们的常见方法：

-  FileReader常见方法：
	1. **int read()**：读取单个字符。返回所读取的字符数据，如果已到达流的末尾，则返回-1。
	2. **int read(char[] cbuf)**：将字符读入数组。返回实际读取的字符数，如果已到达流的末尾，则返回-1。
	3. **int read(char[] cbuf, int off, int len)**：将字符读入数组的某一部分。返回实际读取的字符数，如果已到达流的末尾，则返回-1。
	4. **void close()**：关闭输入流。

-  FileWriter常见方法：
	1. **void write(int c)**：写入单个字符。
	2. **void write(char[] cbuf)**：写入字符数组。
	3. **void write(String str)**：写入字符串。
	4. **void write(char[] cbuf, int off, int len)**：写入字符数组的某一部分。
	5. **void flush()**：刷新输出流，将缓冲区的数据写入目标设备。
	6. **void close()**：关闭输出流。
这里需要额外介绍一下File类，它是专门用于表示一个文件或文件夹，只不过它只是代表这个文件，但并不是这个文件本身。通过File对象，可以更好地管理和操作硬盘上的文件。
File类是Java中用于表示文件和目录路径的类，它提供了一系列方法用于创建、删除、重命名、检查文件和目录等操作。以下是File类的一些常用方法：

1. **File(String pathname)**：根据指定的路径名创建一个File实例。
2. **boolean exists()**：判断文件或目录是否存在。
3. **boolean isFile()**：判断是否是一个文件。
4. **boolean isDirectory()**：判断是否是一个目录。
5. **String getName()**：获取文件或目录的名称。
6. **String getPath()**：获取文件或目录的路径。
7. **long length()**：获取文件的长度（字节数）。
8. **boolean createNewFile()**：创建新文件，如果文件已存在则返回false。
9. **boolean mkdir()**：创建新目录，如果目录已存在则返回false。
10. **boolean delete()**：删除文件或目录。
11. **boolean renameTo(File dest)**：重命名文件或目录为指定的目标文件。
12. **String[] list()**：返回目录下的文件和目录名列表。
13. **File[] listFiles()**：返回目录下的文件和目录列表的File对象数组。
## 缓冲流
虽然普通的文件流读取文件数据非常便捷，但是每次都需要从外部I/O设备去获取数据，由于外部I/O设备的速度一般都达不到内存的读取速度，很有可能造成程序反应迟钝，因此性能还不够高，而缓冲流正如其名称一样，它能够提供一个缓冲，提前将部分内容存入内存（缓冲区）在下次读取时，如果缓冲区中存在此数据，则无需再去请求外部设备。同理，当向外部设备写入数据时，也是由缓冲区处理，而不是直接向外部设备写入。
![[缓冲区.png]]

Java中的缓冲流是对输入流和输出流的包装，通过在输入流和输出流外面包一层缓冲区，可以提高IO操作的效率。Java提供了四种缓冲流：`BufferedInputStream`、`BufferedOutputStream`、`BufferedReader`和`BufferedWriter`。

`BufferedInputStream`的常用方法：
1. `mark(int readlimit)`：在当前位置设置标记，readlimit参数指定在调用reset()方法之前可以读取的最大字节数。
2. `reset()`：将输入流的位置重置到最后一次调用mark()方法时的位置。

`BufferedReader`的常用方法：
1. `readLine()`：读取一行文本。返回包含该行文本内容的字符串，不包括行尾的换行符。如果已经到达流的末尾，则返回null。

## 转换流
转换流是Java IO中的一种流，用于在字节流和字符流之间进行转换。在Java中，通常使用InputStreamReader和OutputStreamWriter来实现字节流到字符流的转换，以便在处理文本数据时能够更方便地使用字符流的特性。
下面是转换流的一些常见用法：

1. `InputStreamReader`：将字节输入流转换为字符输入流。可以指定字符编码来进行转换。
2. `OutputStreamWriter`：将字符输出流转换为字节输出流。同样可以指定字符编码。
3. 使用BufferedReader和BufferedWriter进行转换流的缓冲操作：
4. 关闭转换流时，只需要关闭最外层的包装流即可：

## 打印流
打印流其实我们从一开始就在使用了，比如`System.out`就是一个PrintStream，PrintStream也继承自FilterOutputStream类因此依然是装饰我们传入的输出流，但是它存在自动刷新机制，例如当向PrintStream流中写入一个字节数组后自动调用`flush()`方法。PrintStream也永远不会抛出异常，而是使用内部检查机制`checkError()`方法进行错误检查。最方便的是，它能够格式化任意的类型，将它们以字符串的形式写入到输出流。
```java
public final static PrintStream out = null;
```

可以看到`System.out`也是PrintStream，不过默认是向控制台打印。

我们平时使用的`println`方法就是PrintStream中的方法，它会直接打印基本数据类型或是调用对象的`toString()`方法得到一个字符串，并将字符串转换为字符，放入缓冲区再经过转换流输出到给定的输出流上。
![img](https://s2.loli.net/2022/10/04/w8RKJxLm6Ik5usn.png)
而我们之前使用的Scanner，使用的是系统提供的输入流：

```java
public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);   //系统输入流，默认是接收控制台输入
}
```

我们也可以使用Scanner来扫描其他的输入流：

```java
public static void main(String[] args) throws FileNotFoundException {
    Scanner scanner = new Scanner(new FileInputStream("秘制小汉堡.txt"));  //将文件内容作为输入流进行扫描
}
```

相当于直接扫描文件中编写的内容，同样可以读取。

## 数据流
在 Java 中，数据流（Data Stream）通常指的是用于读取或写入数据的流。Java 中的数据流主要分为两类：输入流（Input Stream）和输出流（Output Stream）。

1. **输入流（Input Stream）**：用于从数据源（如文件、网络连接、内存等）读取数据。在 Java 中，常见的输入流包括 `FileInputStream`、`DataInputStream`、`ObjectInputStream` 等，它们可以用来读取文件、读取基本数据类型、读取对象等。
    
2. **输出流（Output Stream）**：用于向目标（如文件、网络连接、内存等）写入数据。常见的输出流包括 `FileOutputStream`、`DataOutputStream`、`ObjectOutputStream` 等，它们可以用来向文件写入数据、写入基本数据类型、写入对象等。

## 对象流
在Java中，对象流是Java I/O库中的一部分，用于在输入输出流中读取和写入对象。对象流提供了一种方便的方式来将对象序列化为字节流，或者将字节流反序列化为对象。主要的对象流包括ObjectInputStream和ObjectOutputStream。

### ObjectInputStream
ObjectInputStream类用于从输入流中读取对象。它可以读取通过ObjectOutputStream写入的对象，并将其反序列化为Java对象。要使用ObjectInputStream，你需要将它与一个输入流（如FileInputStream或SocketInputStream）结合使用。
### ObjectOutputStream
ObjectOutputStream类用于将对象写入输出流。它可以将Java对象序列化为字节流，并将其写入到输出流中。要使用ObjectOutputStream，你需要将它与一个输出流（如FileOutputStream或SocketOutputStream）结合使用。

### 序列化
在Java中，序列化是指将对象转换为字节流的过程，以便可以将其保存到文件、数据库或者通过网络传输。反之，反序列化则是将字节流转换回对象的过程。Java提供了序列化和反序列化的机制，使得对象可以在不同的环境中进行传输和持久化。
要实现序列化，需要满足以下条件：
1. 类必须实现java.io.Serializable接口，这是一个标记接口，没有任何方法。
2. 所有的成员变量必须是可序列化的，或者标记为transient，表示不需要序列化。

