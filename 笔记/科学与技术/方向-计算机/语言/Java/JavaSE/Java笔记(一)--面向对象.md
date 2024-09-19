---
aliases:
  - Java1
tags: 
data: 2024-05-31
---
# 类与对象
类，如：人类、鸟类、鱼类... 所谓类，就是对一类事物的描述，是抽象的、概念上的定义。
对象，是某一类事物实际存在的每个个体，因而也被称为实例（instance）我们每个人都是人类的一个实际存在的个体。  
Java中，我们可以定义一个类，然后进一步创建许多这个类的实例对象。像这种编程方式，我们称为**面向对象编程**。

## 一.类的创建

类有两大特性，属性与方法。属性记录类的具体数据，能力等。方法是对某一行为的具体实现(类似于面向过程编程中的方法)

### 创建属性
创建属性一般在卸载类的开头，可以用各种各样的基本数据类型或对象来定义当前类的属性
```java
public class Person {   //这里定义的人类具有三个属性，名字、年龄、性别
    String name;   //直接在类中定义变量，表示类具有的属性
    int age;
    String sex;
}
```
一般的属性包括两种：
1. 一般属性  
2. 静态属性  
静态属性会在全局保持一致，不管在哪个对象中都是一个样，而一般属性在一个对象中被更改只影响本对象。
  
### 创建方法
创建方法的方式与函数类似
```
返回值类型 方法名称() {
		方法体...
}
```
类的种类我大体分为四种：
1. 一般方法：
	- 最基本的方法，没有什么特殊性。
2. 静态方法：
	- 静态不需要创建对象，用类名即可调用。可在可作用域全局使用。
3. 抽象方法：
	 -  抽象方法不含有方法本身，通过具体实现完成(需要重写)。
4. 构造方法：
	 -  名字与类名相同，用于[[Java笔记(一)--面向对象#^69699e|初始化对象]]。

## 二.类的使用

^69699e

在使用类之前需要对类实体化，必须用 ‘new’ 来实体化某一个类
```java
public static void main(String[] args) {
    Person p1 = new Person();
    Person p2 = p1; //p1与p2指向的是同一个类
}
```
通过' .' 可以调用到对象的属性和方法。
```java
public static void main(String[] args) {
    Person p = new Person();
    p.name = "小明";   //要访问对象的属性，我们需要使用 . 运算符
    System.out.println(p.name);   //直接打印对象的名字，就是我们刚刚修改好的结果了
}
```
```java
public static void main(String[] args) {
    Person p = new Person();
    p.setName("小明");
    System.out.println(p.name);
}
```
### 数据类型类
在Java中借助类的工具，可以使我们的数据类型变得更加强大！
所有的基本数据类型都被包装成了一个功能强大的包装类。
所有的包装类层次结构如下：
![[基本数据类型的继承关系.png]]
1. Integer类：
- **属性**：
    - MAX_VALUE：int类型的最大值。
    - MIN_VALUE：int类型的最小值。
- **方法**：
    - parseInt(String s)：将字符串转换为int类型。
    - valueOf(int i)：返回一个表示指定int值的Integer实例。
    - toString()：将Integer对象转换为String。
    - intValue()：返回Integer对象的int值。
    - compareTo()：比较两个Integer对象的值
2. Double类：
- **属性**：
    - MAX_VALUE：double类型的最大值。
    - MIN_VALUE：double类型的最小正数值。
    - NaN：表示不是一个数字。
    - POSITIVE_INFINITY：正无穷大。
    - NEGATIVE_INFINITY：负无穷大。
- **方法**：
    - parseDouble(String s)：将字符串转换为double类型。
    - valueOf(double d)：返回一个表示指定double值的Double实例。
    - toString()：将Double对象转换为String。
    - doubleValue()：返回Double对象的double值。
    - compareTo()：比较两个Double对象的值。
3.  Boolean类：
 - **方法**：
        - parseBoolean(String s)：将字符串转换为boolean类型。
        - valueOf(boolean b)：返回一个表示指定boolean值的Boolean实例。
        - toString()：将Boolean对象转换为String。
        - booleanValue()：返回Boolean对象的boolean值。
        - compareTo()：比较两个Boolean对象的值。
4.  Character类：
- **方法**：
    - isLetter(char c)：判断字符是否为字母。
    - isDigit(char c)：判断字符是否为数字。
    - isWhitespace(char c)：判断字符是否为空白字符。
    - toUpperCase(char c)：将字符转换为大写形式。
    - toLowerCase(char c)：将字符转换为小写形式。  
5. Long类：
- **属性**：
    - MAX_VALUE：long类型的最大值。
    - MIN_VALUE：long类型的最小值。
- **方法**：
    - parseLong(String s)：将字符串转换为long类型。
    - valueOf(long l)：返回一个表示指定long值的Long实例。
    - toString()：将Long对象转换为String。
    - longValue()：返回Long对象的long值。
    - compareTo()：比较两个Long对象的值。
6. Float类：
  - **属性**：
    - MAX_VALUE：float类型的最大正数值。
    - MIN_VALUE：float类型的最小正数值。
    - NaN：表示不是一个数字。
    - POSITIVE_INFINITY：正无穷大。
    - NEGATIVE_INFINITY：负无穷大。
 - **方法**：
    - parseFloat(String s)：将字符串转换为float类型。
    - valueOf(float f)：返回一个表示指定float值的Float实例。
    - toString()：将Float对象转换为String。
    - floatValue()：返回Float对象的float值。
    - compareTo()：比较两个Float对象的值。
#### 装箱与拆箱：
在包装类中:允许 int x =Integer y 的语法存在。因为包装类能自动拆箱，使包装类"拆"成基本数据
而基本数据又可以直接转为包装类。因为包装类可以自动装箱。
> 自动装箱的一个简例
```java 
public static void main(String[] args) {
    Integer i = 10;
	Integer i = Integer.valueOf(10);    //上面的写法跟这里是等价的
}
```

#### 特殊包装类
1. **BigDecimal类**：
	- **常用属性：**
		1. **ZERO**：表示值为0的BigDecimal常量。
		2. **ONE**：表示值为1的BigDecimal常量。
		3. **TEN**：表示值为10的BigDecimal常量。
	-  **常用方法：**
	    1. **add(BigDecimal value)**：将当前BigDecimal对象与指定的BigDecimal值相加。
		2. **subtract(BigDecimal value)**：用指定的BigDecimal值减去当前BigDecimal对象的值。
		3. **multiply(BigDecimal value)**：将当前BigDecimal对象与指定的BigDecimal值相乘。
		4. **divide(BigDecimal value)**：将当前BigDecimal对象除以指定的BigDecimal值，返回商，使用指定的舍入模式。
		5. **compareTo(BigDecimal value)**：将当前BigDecimal对象与指定的BigDecimal值进行比较，返回-1、0或1，表示小于、等于或大于。
		6. **setScale(int newScale, RoundingMode roundingMode)**：设置BigDecimal对象的精度（小数位数）并使用指定的舍入模式。
		7. **intValue()、longValue()、doubleValue()、floatValue()**：将BigDecimal对象转换为int、long、double、float类型。
		8. **abs()**：返回BigDecimal对象的绝对值。
		9. **stripTrailingZeros()**：去除BigDecimal对象尾部多余的零。
2. **BigInteger类**：
	-  **常用属性：**
		1. **ZERO**：表示值为0的BigInteger常量。
		2. **ONE**：表示值为1的BigInteger常量。
		3. **TEN**：表示值为10的BigInteger常量。
	-  **常用方法：**

		1. **add(BigInteger value)**：将当前BigInteger对象与指定的BigInteger值相加。
		2. **subtract(BigInteger value)**：用指定的BigInteger值减去当前BigInteger对象的值。
		3. **multiply(BigInteger value)**：将当前BigInteger对象与指定的BigInteger值相乘。    
		4. **divide(BigInteger value)**：将当前BigInteger对象除以指定的BigInteger值，返回商。
		5. **remainder(BigInteger value)**：返回当前BigInteger对象除以指定的BigInteger值的余数。    
		6. **compareTo(BigInteger value)**：将当前BigInteger对象与指定的BigInteger值进行比较，返回-1、0或1，表示小于、等于或大于。    
		7. **pow(int exponent)**：返回当前BigInteger对象的指数幂。
		8. **intValue()、longValue()、doubleValue()**：将BigInteger对象转换为int、long、double类型。
		9. **abs()**：返回BigInteger对象的绝对值。
		10. **gcd(BigInteger value)**：返回当前BigInteger对象与指定的BigInteger值的最大公约数。
3. **Optional类**：
    - **常用属性：**
		1. **EMPTY**：表示一个空的Optional对象，即不包含值。
	- **常用方法：**
		1. **of(T value)**：创建一个包含指定值的Optional对象，如果指定的值为null，则抛出NullPointerException异常。
		2. **ofNullable(T value)**：创建一个包含指定值的Optional对象，如果指定的值为null，则返回一个空的Optional对象。
		3. **empty()**：返回一个空的Optional对象。    
		4. **isPresent()**：如果Optional对象包含非null的值，则返回true，否则返回false。
		5. **ifPresent(Consume\< ? super T> consumer)**：如果Optional对象包含非null的值，则对该值执行指定操作。
		6. **get()**：如果Optional对象包含非null的值，则返回该值，否则抛出NoSuchElementException异常。
		7. **orElse(T other)**：如果Optional对象包含非null的值，则返回该值，否则返回指定的默认值。
		8. **orElseGet(Supplier\< ? extends T> other)**：如果Optional对象包含非null的值，则返回该值，否则使用指定的Supplier提供的值作为默认值。
		9. **orElseThrow(Supplier\< ? extends X> exceptionSupplier)**：如果Optional对象包含非null的值，则返回该值，否则抛出由指定Supplier提供的异常。  
		10. **map(Function\< ? super T, ? extends U> mapper)**：如果Optional对象包含非null的值，则对该值进行映射操作，返回一个包含映射结果的Optional对象。
		11. **filter(Predicate\< ? super T> predicate)**：如果Optional对象包
4. **Enum类**：
	-  **常用属性：**
		1. **name**：枚举常量的名称，以字符串形式返回。
		2. **ordinal**：枚举常量的位置索引，从0开始计数。
	-   **常用方法：**
		1. **valueOf(String name)**：根据枚举常量的名称返回对应的枚举常量。    
		2. **values()**：返回一个包含所有枚举常量的数组。
		3. **compareTo(E o)**：比较枚举常量的顺序，返回值为负数、零或正数，表示当前枚举常量小于、等于或大于指定枚举常量。
		4. **name()**：返回枚举常量的名称。
		5. **ordinal()**：返回枚举常量的位置索引。
		6. **toString()**：返回枚举常量的名称，与name()方法作用相同。
		7. **valueOf(Class\< T> enumType, String name)**：根据指定枚举类型和枚举常量的名称返回对应的枚举常量。
		8. **getDeclaringClass()**：返回枚举常量的Class对象，即定义该枚举常量的枚举类。
		9. **equals(Object other)**：比较枚举常量是否与指定对象相等。
### 数组类
#### 数组的创建：
1. **声明数组变量：** 需要先声明一个数组变量来引用数组对象。
    `int[] myArray;`
2. **创建数组对象：** 使用`new`关键字创建数组对象，并指定数组的长度。
    `myArray = new int[5];`
3. **直接创建并初始化数组：** 也可以一步到位地创建并初始化数组。    
    `int[] myArray = {1, 2, 3, 4, 5};`
#### 数组的常用属性与方法
- 常用属性：
	1. **length：** 数组的长度属性，表示数组中元素的个数。
-  常用方法：
	1. **clone()：** 复制数组，创建并返回一个数组的副本。    
	2. **toString()：** 将数组转换为字符串，返回包含数组元素的字符串表示。    
	3. **sort()：** 对数组进行排序。
	4. **equals()：** 比较两个数组是否相等。
	5. **fill()：** 将数组的所有元素设置为指定值。
### 字符串
#### String类
- 常用属性：
	1. **length()：** 返回字符串的长度。
- 常用方法：
	1. **charAt()：** 返回指定索引处的字符。
	2. **substring()：** 返回一个新的字符串，从指定的起始索引开始，直到字符串末尾。
	3. **substring(int beginIndex, int endIndex)：** 返回一个新的字符串，包含从beginIndex开始到endIndex-1的字符。   
	4. **toUpperCase()：** 将字符串转换为大写。
	5. **toLowerCase()：** 将字符串转换为小写。
	6. **equals()：** 比较字符串内容是否相等。
	7. **equalsIgnoreCase(String anotherString)：** 忽略大小写比较字符串内容是否相等。
	8. **indexOf()：** 返回指定字符在字符串中第一次出现的位置索引。
	9. **lastIndexOf(int ch)：** 返回指定字符在字符串中最后一次出现的位置索引。
	10. **replace()：** 将字符串中的指定字符或字符串替换为新的字符或字符串。
	11. **concat(String str)**：将指定字符串连接到原字符串的末尾
	12. **startsWith(String prefix)：** 判断字符串是否以指定前缀开头。
	13. **endsWith(String suffix)：** 判断字符串是否以指定后缀结尾。
	14. **split(String regex)：** 根据给定正则表达式拆分字符串为字符串数组。
	15. **contains(CharSequence s)：** 判断字符串是否包含指定字符序列。
	16. **isEmpty()：** 判断字符串是否为空。
	17. **valueOf()：** 将其他数据类型转换为字符串。
####  StringBuilder类
-  常用属性：
	1. **char[] value**：用于存储字符串内容的字符数组。
	2. **int count**：当前字符串的长度。
	3. **int capacity**：当前StringBuilder对象的容量。
-  常用方法：
	1. **StringBuilder()**：构造一个空的StringBuilder对象。
	2. **StringBuilder(CharSequence seq)**：使用指定的字符序列构造一个StringBuilder对象。
	3. **int length()**：返回当前StringBuilder对象中字符序列的长度。
	4. **int capacity()**：返回当前StringBuilder对象的容量。
	5. **void ensureCapacity(int minimumCapacity)**：确保StringBuilder对象的容量至少为指定值。
	6. **StringBuilder append(String str)**：将指定字符串追加到当前StringBuilder对象的末尾。
	7. **StringBuilder append(char c)**：将指定字符追加到当前StringBuilder对象的末尾。
	8. **StringBuilder insert(int offset, String str)**：在指定位置插入指定字符串。
	9. **StringBuilder delete(int start, int end)**：删除指定范围内的字符。
	10. **StringBuilder deleteCharAt(int index)**：删除指定位置的字符。
	11. **StringBuilder replace(int start, int end, String str)**：用新字符串替换指定范围内的字符。
	12. **StringBuilder reverse()**：将StringBuilder对象中的字符序列进行反转。
	13. **void setCharAt(int index, char ch)**：将指定位置的字符设置为指定字符。
	14. **String substring(int start)**：返回从指定位置开始到结尾的子字符串。
	15. **String substring(int start, int end)**：返回指定范围内的子字符串。
	16. **void setLength(int newLength)**：设置StringBuilder对象的长度。
	17. **void trimToSize()**：将StringBuilder对象的容量调整为当前字符串长度的大小。
	18. **char charAt(int index)**：返回指定位置的字符。
	19. **void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)**：将指定范围内的字符复制到目标数组中。
	20. **int indexOf(String str)**：返回指定字符串在当前StringBuilder对象中第一次出现的位置。
	21. **int lastIndexOf(String str)**：返回指定字符串在当前StringBuilder对象中最后一次出现的位置。
### 可变长参数
- 定义语法：
	```
	public void methodName(Type... parameterName) { // 方法体 }
	```
- 注意事项
	- 1.可变长参数必须是方法的最后一个参数
	- 2.在方法内部，可变长参数被当作数组处理
	- 3.如果方法有多个参数，可变长参数可以接受零个或多个参数，但每次调用方法时只能传递一个可变长参数
	- 4.如果方法的参数列表中有多个参数，可变长参数只能出现一次

### 内部类
在Java中，内部类是定义在另一个类内部的类。内部类的主要作用是可以访问包含它的外部类的成员变量和方法，同时可以隐藏实现细节，提高代码的封装性和可读性。根据内部类的定义位置和特点，可以分为以下几种类型(仅需知道叫什么就行)：
1. **成员内部类（Member Inner Class）**：
    - 成员内部类是定义在一个类内部的普通类，可以访问外部类的所有成员变量和方法。
    - 成员内部类可以使用外部类的实例来创建对象，例如：OuterClass.InnerClass innerObject = outerObject.new InnerClass();
    - 成员内部类可以被声明为private、protected、public或默认访问权限。
2. **静态内部类（Static Nested Class）**：
    - 静态内部类是使用static关键字修饰的内部类，与外部类实例无关，不持有外部类的引用。
    - 静态内部类可以直接通过外部类名访问，例如：OuterClass.StaticInnerClass innerObject = new OuterClass.StaticInnerClass();
    - 静态内部类不能访问外部类的非静态成员，只能访问外部类的静态成员。
    - 一般用于工具类的创建
3. **局部内部类（Local Inner Class）**：
    - 局部内部类是定义在方法内部的类，作用域仅限于所在方法内部。
    - 局部内部类可以访问方法内的局部变量，但是局部变量必须是final或事实上的final（即不可再赋值）。
    - 局部内部类不能使用访问控制修饰符（private、protected、public）。
4. **匿名内部类（Anonymous Inner Class）**：
    - 匿名内部类是一种没有类名的内部类，通常用于创建只需使用一次的类的实例。
    - 匿名内部类通常在创建对象的同时进行类的定义和实例化，简化代码结构。
    - 匿名内部类可以实现接口、继承抽象类或直接实例化类，并重写其中的方法。
#### Lambda表达式(代替匿名内部类)
Lambda表达式是Java 8 中引入的一个重要特性，它允许我们以更简洁的方式编写匿名函数。Lambda表达式主要用于简化使用函数式接口的代码，可以替代使用匿名内部类的方式来实现函数式接口的方法。

- Lambda表达式的语法：
```
(parameters) -> expression 或 (parameters) -> { statements; }
````
- 参数列表：可以是空的，或者包含一个或多个参数。
- 箭头符号 `->`：分隔参数列表和Lambda表达式的主体。
- Lambda表达式主体：可以是一个表达式或一段代码块。


### 常见工具类
在Java中编程，有许许多多的工具类，他们的一些属性和方法可以帮助我们简化流程，让我们更好地实现功能
#### 数学工具类
##### Math类
-  常用常量：
	- `Math.PI`：表示圆周率 π 的常量。
	- `Math.E`：表示自然对数的底 e 的常量。
- 常用方法：
	- 1. **数学函数**：
	    - `abs(int a)`：返回参数的绝对值。
	    - `max(int a, int b)`：返回两个参数中较大的值。
	    - `min(int a, int b)`：返回两个参数中较小的值。
	    - `sqrt(double a)`：返回参数的平方根。
	    - `pow(double a, double b)`：返回 a 的 b 次幂。
	    - `sin(double a)`：返回参数的正弦值（参数为弧度）。
	    - `cos(double a)`：返回参数的余弦值（参数为弧度）。
	    - `tan(double a)`：返回参数的正切值（参数为弧度）。
	    - `log(double a)`：返回参数的自然对数（以 e 为底）。
	    - `exp(double a)`：返回 e 的 a 次幂。
	2. **取整函数**：
	    - `ceil(double a)`：返回大于等于参数的最小整数。
	    - `floor(double a)`：返回小于等于参数的最大整数。
	    - `round(double a)`：返回最接近参数的 long 值，四舍五入。
	3. **其他方法**：(一般不用，直接用Random类)
	    - `random()`：返回一个大于等于 0.0 且小于 1.0 的随机 double 值。
##### Random类
- 常用方法：
	1. **生成随机整数**：
	    - `nextInt()`：生成一个随机的整数。
	    - `nextInt(int bound)`：生成一个大于等于 0 且小于 bound 的随机整数。
	    - `nextInt(int min, int max)`：生成一个在\[min, max\]范围内的随机整数。
	2. **生成随机浮点数**：
	    - `nextDouble()`：生成一个大于等于 0.0 且小于 1.0 的随机浮点数。
	    - `nextFloat()`：生成一个大于等于 0.0 且小于 1.0 的随机浮点数。
	3. **生成随机布尔值**：
	    - `nextBoolean()`：生成一个随机的布尔值。
	4. **生成随机字节数组**：
	    - `nextBytes(byte[] bytes)`：生成随机的字节数组，填充到给定的字节数组中。


#### 日期类
##### Data类
- 常用属性：
	1. **`long time`**：表示自 1970 年 1 月 1 日 00:00:00 GMT 以来的毫秒数，即时间戳。
- 常用方法：
	1. **`Date()`**：无参构造方法，创建一个`Date`对象，表示当前日期时间。
	2. **`Date(long date)`**：根据指定的时间戳创建一个`Date`对象。
	3. **`getTime()`**：返回该`Date`对象的时间戳（毫秒数）。
	4. **`setTime(long time)`**：设置该`Date`对象的时间戳。
	5. **`before(Date when)`**：判断该`Date`对象表示的日期时间是否在`when`之前。
	6. **`after(Date when)`**：判断该`Date`对象表示的日期时间是否在`when`之后。
	7. **`equals(Object obj)`**：判断该`Date`对象与指定对象是否相等。
	8. **`toString()`**：将`Date`对象转换为字符串表示形式，一般为日期时间的字符串。
##### Calendar类
- 常用属性：
	1. **`YEAR`、`MONTH`、`DATE`、`HOUR_OF_DAY`、`MINUTE`、`SECOND`**：表示年、月、日、小时、分钟、秒等字段的常量。
	2. **`DAY_OF_WEEK`、`DAY_OF_MONTH`、`DAY_OF_YEAR`**：表示星期几、月中的第几天、年中的第几天等字段的常量。
- 常用方法：
	1. **`getInstance()`**：静态方法，返回一个`Calendar`对象，表示当前日期时间。
	2. **`get(int field)`**：获取指定字段的值，如年、月、日等。
	3. **`set(int field, int value)`**：设置指定字段的值。
	4. **`add(int field, int amount)`**：将指定字段的值增加指定的数量。
	5. **`getTime()`**：返回表示该`Calendar`对象日期时间的`Date`对象。
	6. **`setTime(Date date)`**：设置该`Calendar`对象的日期时间。
	7. **`clear()`**：清除该`Calendar`对象的所有字段值。
	8. **`getActualMaximum(int field)`**：获取指定字段的最大值，如某月的最大天数。
	9. **`getActualMinimum(int field)`**：获取指定字段的最小值。
	10. **`isLeapYear(int year)`**：判断指定年份是否是闰年。
##### LocalDate类
- 常见属性：
	1. **`year`**：年份。
	2. **`month`**：月份。
	3. **`dayOfMonth`**：月中的第几天。
	4. **`dayOfWeek`**：星期几。
	5. **`dayOfYear`**：年中的第几天。
- 常见方法：
	1. **`now()`**：静态方法，返回当前日期。
	2. **`of(int year, int month, int dayOfMonth)`**：静态方法，根据指定的年、月、日创建`LocalDate`对象。
	3. **`getYear()`**：获取年份。
	4. **`getMonth()`**：获取月份。
	5. **`getDayOfMonth()`**：获取月中的第几天。
	6. **`getDayOfWeek()`**：获取星期几。
	7. **`getDayOfYear()`**：获取年中的第几天。
	8. **`plusDays(long daysToAdd)`**：增加指定天数。
	9. **`plusMonths(long monthsToAdd)`**：增加指定月数。
	10. **`plusYears(long yearsToAdd)`**：增加指定年数。
	11. **`minusDays(long daysToSubtract)`**：减去指定天数。
	12. **`minusMonths(long monthsToSubtract)`**：减去指定月数。
	13. **`minusYears(long yearsToSubtract)`**：减去指定年数。
	14. **`isEqual(LocalDate other)`**：判断是否与另一个`LocalDate`相等。
	15. **`isAfter(LocalDate other)`**：判断是否在另一个`LocalDate`之后。
	16. **`isBefore(LocalDate other)`**：判断是否在另一个`LocalDate`之前。
	17. **`format(DateTimeFormatter formatter)`**：将日期格式化为指定格式的字符串。
# 方法
## 一.方法的创建
### 构造方法
在 Java 中，构造方法是一种特殊的方法，用于创建对象时初始化对象的实例变量。构造方法的特点如下：
1. 构造方法的名称必须与类名相同。
2. 构造方法没有返回类型，甚至没有`void`。
3. 构造方法在使用`new`关键字创建对象时被调用。
4. 如果一个类没有定义任何构造方法，Java 会提供一个默认的无参构造方法。
5. 如果一个类定义了构造方法，但没有定义无参构造方法，Java 不会再提供默认的无参构造方法。
6. 一个类可以有多个构造方法，只要它们的参数列表不同（重载）。
7. 构造方法可以被重载，即在同一个类中可以定义多个参数列表不同的构造方法。
### 方法的重载

^58567a

在Java中，方法的重载（Overloading）是指在同一个类中可以存在多个方法，它们具有相同的方法名但参数列表不同的情况。方法的重载可以通过改变方法的参数个数、类型或顺序来实现。
### 静态方法与静态变量
在Java中，静态方法和静态变量是与类相关联而不是与类的实例（对象）相关联的。
#### 静态方法（Static Methods）：
1. **静态方法属于类而不是对象：** 静态方法是类级别的方法，可以直接通过类名调用，无需创建类的实例。
2. **不能访问非静态成员：** 静态方法中不能直接访问非静态成员变量和非静态方法，因为非静态成员是依赖于对象存在的。
3. **可以访问静态成员：** 静态方法可以直接访问类的静态成员变量和静态方法。
4. **静态方法中不能使用this关键字：** 静态方法中不能使用this关键字，因为this代表当前对象，而静态方法是属于类的，没有this对象。
#### 静态变量（Static Variables）：
1. **静态变量属于类而不是对象：** 静态变量是类级别的变量，所有实例共享同一份静态变量。
2. **静态变量在类加载时初始化：** 静态变量在类加载时会被初始化，并且只会被初始化一次。
3. **可以直接通过类名访问：** 可以通过类名直接访问静态变量，无需创建类的实例。
4. **静态变量通常用于表示类级别的信息：** 静态变量通常用于表示类级别的信息，如常量、计数器等。
## 二.对象的创建
在使用类之前需要对类实体化，必须用 ‘new’ 来实体化某一个类
```java
public static void main(String[] args) {
    Person p1 = new Person();
    Person p2 = p1; //p1与p2指向的是同一个类
}
```
## 三.方法的使用
```java
public static void main(String[] args) {
    Person p = new Person();
    p.name = "小明";   //要访问对象的属性，我们需要使用 . 运算符
    System.out.println(p.name);   //直接打印对象的名字，就是我们刚刚修改好的结果了
}
```
```java
public static void main(String[] args) {
    Person p = new Person();
    p.setName("小明");
    System.out.println(p.name);
}
```

# 包
## 声明与导入
在Java中，包（Package）是用来组织和管理类的命名空间的机制，可以将相关的类组织在一起，避免命名冲突，并提供更好的代码结构。
### 包的声明（Package Declaration）：
1. **包的声明语法：** 在Java源文件的第一行可以使用`package`关键字声明包，语法如下：
    `package com.example.mypackage;`
    这个声明将该源文件放置在名为`com.example.mypackage`的包中。
2. **包名规范：** 包名通常是小写字母，并且使用`.`作为分隔符，按照域名倒序的方式命名，例如`com.example.mypackage`。
3. **包的层级关系：** 包可以有多级层次，比如`com.example.mypackage`是一个三级包，其中`com`是顶级包。
4. **默认包：** 如果没有使用`package`关键字声明包，那么类将位于默认包中，但不建议在实际开发中使用默认包。
### 包的导入（Import）：
1. **导入单个类：** 使用`import`关键字导入单个类，语法如下：
    `import com.example.mypackage.MyClass;`
2. **导入整个包：** 使用`import`关键字导入整个包，语法如下：
    `import com.example.mypackage.*;`
3. **静态导入：** 使用`import static`关键字可以静态导入类的静态成员，语法如下：
    `import static java.lang.Math.*;`
4. **导入的位置：** 导入语句通常放在包声明之后，类定义之前。
5. **重复导入：** 在同一个文件中可以多次导入同一个类，但不会有任何影响。
## java.lang包
`java.lang`包是Java编程语言的核心包之一，它包含了Java语言的核心类和基本类型的支持。`java.lang`包中的类是Java编程中最常用的类，无需显式导入即可直接使用。下面介绍一些`java.lang`包中常用的类和功能：
-  常用类和功能：
1. **Object类：** `Object`类是所有Java类的父类，包含了所有Java对象共有的方法，如`equals()`, `hashCode()`, `toString()`等。
2. **String类：** `String`类用于表示字符串，提供了丰富的字符串操作方法，如拼接、截取、替换等。
3. **Integer、Double、Boolean等包装类：** 这些类用于封装Java基本数据类型，提供了一些便捷的方法和属性。
4. **System类：** `System`类提供了标准输入、输出、错误流，以及一些系统级的方法和属性，如`currentTimeMillis()`获取当前时间毫秒数。
5. **Math类：** `Math`类提供了数学计算相关的静态方法，如常见的数学运算、三角函数等。
6. **Thread类：** `Thread`类用于创建和操作线程，实现多线程编程。
7. **Runtime类：** `Runtime`类允许Java应用程序与运行时环境进行交互，如执行外部程序、获取系统信息等。
8. **Exception类及其子类：** `Exception`类是所有异常的父类，它的子类如`RuntimeException`、`IOException`等用于处理不同类型的异常。
9. **ClassLoader类：** `ClassLoader`类用于动态加载Java类，实现类的动态加载和管理。
# 代码块
在Java中任何一段代码都是在代码块中实现和完成的，代码块标明了代码的作用域与虚拟机的执行顺序。下面介绍常见的代码块：
## 静态代码块
在Java中，静态代码块是用关键字`static`定义的一种特殊代码块，它在类加载时会被执行，且只会执行一次。静态代码块通常用于在类加载时进行一些初始化操作，如初始化静态变量、加载资源等。下面是关于静态代码块的一些重要特点和示例：
### 特点：
1. **关键字：** 静态代码块使用`static`关键字定义。
2. **执行时机：** 静态代码块在类加载时执行，且只会执行一次。
3. **执行顺序：** 静态代码块的执行顺序与其在类中的位置有关，按照代码在类中的顺序依次执行。
4. **无需实例化：** 静态代码块不依赖于类的实例，可以直接通过类名调用。
5. **可以有多个：** 一个类可以有多个静态代码块，它们按照在类中的顺序依次执行。

静态代码块通常用于进行一些静态资源的初始化工作，或者在类加载时执行一些必要的操作。需要注意的是，静态代码块的执行是在类加载时进行的，如果一个类从未被使用过，那么其中的静态代码块也不会被执行。
## 实例代码块
在Java中，实例代码块（Instance Initializer Block）是一种用于对象初始化的代码块，它在创建对象时被调用，每次创建对象时都会执行。实例代码块用于在对象创建时进行一些初始化操作，类似于构造方法，但实例代码块不是构造方法的一部分。下面是关于实例代码块的一些重要特点和示例：
### 特点：
1. **位置：** 实例代码块位于类中，没有任何方法名或参数列表，使用一对花括号括起来。
2. **执行时机：** 实例代码块在每次创建对象时执行，优先于构造方法执行。
3. **执行顺序：** 实例代码块的执行顺序与其在类中的位置有关，按照代码在类中的顺序依次执行。
4. **与构造方法的关系：** 实例代码块不是构造方法的一部分，但在创建对象时会先执行实例代码块，再执行构造方法。
实例代码块通常用于在对象创建时进行一些初始化操作，可以在其中进行一些复杂的初始化逻辑或者对实例变量进行赋值操作。需要注意的是，实例代码块在每次创建对象时都会执行，因此它适用于需要在对象创建时进行初始化的场景。
## 同步代码块
在Java中，同步代码块和同步方法都是用来实现线程同步的机制，可以确保多个线程安全地访问共享资源。它们都是为了解决多线程并发访问共享资源时可能出现的数据不一致或竞态条件的问题。下面分别介绍同步代码块和同步方法的特点和用法：
### 同步代码块：
1. **特点：**
    - 使用关键字 `synchronized` 来定义同步代码块。
    - 同步代码块使用一个对象作为锁，只有获取到该对象的线程才能执行同步代码块。
    - 同步代码块的粒度比较细，可以指定需要同步的代码块，提高程序的执行效率。
### 同步方法：
1. **特点：**
    - 使用关键字 `synchronized` 来定义同步方法。
    - 整个方法体都被同步，只有一个线程能够执行同步方法，其他线程需要等待。
    - 同步方法的粒度比较粗，适用于整个方法需要同步的情况。
### 区别：
- **粒度不同：** 同步代码块的粒度可以更细，只同步需要同步的代码块，而同步方法的粒度较粗，整个方法都会被同步。
- **锁的对象不同：** 同步代码块可以指定任意对象作为锁，而同步方法使用的是当前对象（this）作为锁。
- **适用场景不同：** 同步代码块适合对特定的代码块进行同步控制，提高程序的执行效率；同步方法适合整个方法需要同步的情况，简单方便。
## 标签
在Java中，代码块标签（Block Label）是一种标识符，用于标记代码块（包括循环、条件语句、方法等）以便在嵌套的代码块中进行跳转操作。通过代码块标签，可以在嵌套的代码块中使用`break`、`continue`、`return`等语句跳转到指定的代码块。
### 注意事项：
- 代码块标签通常用于多层嵌套循环或条件语句中，帮助在内层代码块中跳转到外层代码块。
- 使用代码块标签时，需要注意代码的可读性，避免过度使用标签导致代码难以理解。
- 在实际开发中，尽量避免使用过多的代码块标签，可以考虑通过重构代码来减少代码块标签的使用。

通过代码块标签，可以在复杂的嵌套代码块中实现灵活的控制流程，但同时也需要谨慎使用，以确保代码的可读性和维护性。
# 访问控制权限
在Java中，访问控制权限是通过访问修饰符（Access Modifier）来实现的，用于控制类、方法、变量等成员的访问权限。Java中有四种访问修饰符，分别是`public`、`protected`、`default`（包级访问权限，默认访问权限）和`private`，它们分别表示不同的访问级别。下面是这四种访问修饰符的具体介绍：

### 1. public：

- **访问范围：** 对所有类可见，无访问限制。
- **示例：** 其他类可以访问被`public`修饰的类、方法、变量。

### 2. protected：

- **访问范围：** 对同一包内的类和所有子类可见。
- **示例：** 子类可以访问被`protected`修饰的方法和变量，不同包的类不能访问。

### 3. default（包级访问权限）：

- **访问范围：** 仅对同一包内的类可见，不使用任何访问修饰符时，默认为包级访问权限。
- **示例：** 同一包内的类可以访问被默认修饰的类、方法、变量，不同包的类不能访问。

### 4. private：

- **访问范围：** 仅对本类可见，其他类无法访问。
- **示例：** 只有本类中可以访问被`private`修饰的方法和变量。

### 访问权限总结：

- `public`：最宽松的访问权限，对所有类可见。
- `protected`：对同一包内的类和所有子类可见。
- `default`：对同一包内的类可见，包级访问权限。
- `private`：仅对本类可见。

在实际开发中，根据需求和设计原则，合理选择合适的访问修饰符来控制类成员的访问权限，以确保程序的安全性和良好的封装性。合理的访问控制权限有助于降低耦合度，提高代码的可维护性和安全性。
# 封装，继承与多态
## 封装
在Java中，封装（Encapsulation）是面向对象编程的三大特性之一，用于将类的数据（属性）和方法（行为）封装在一起，同时对外部隐藏对象的内部实现细节，通过公共的方法提供对对象的访问。封装可以提高代码的安全性、可维护性和可重用性，同时实现了信息隐藏和数据保护。下面是封装的主要特点和实现方式：

### 封装的特点：

1. **数据隐藏：** 将对象的属性隐藏起来，只能通过类提供的方法来访问和修改数据，避免外部直接访问对象的属性。
2. **访问控制：** 通过访问修饰符（`private`、`public`、`protected`、`default`）控制类的成员的访问权限，提供对外部的安全访问接口。
3. **数据封装：** 将数据和操作数据的方法封装在一起，形成一个类，实现了数据和行为的统一管理。

### 实现封装的方式：

1. **使用私有访问修饰符（`private`）：** 将类的成员变量设置为`private`，限制外部直接访问。
    
2. **提供公共方法（Getter和Setter）：** 通过公共方法（Getter和Setter）来访问和修改私有成员变量，实现对数据的控制和操作。
##  继承
在Java中，继承（Inheritance）是面向对象编程的三大特性之一，允许一个类（子类）继承另一个类（父类）的属性和方法。子类可以继承父类的非私有属性和方法，并且可以通过扩展（添加新的属性和方法）和重写（覆盖父类的方法）来实现代码的复用和扩展。下面是关于Java中继承的一些重要概念和特点：
-  继承的特点：
1. **代码复用：** 子类可以继承父类的属性和方法，避免重复编写相同的代码。
2. **派生性：** 子类可以派生出新的子类，形成类的层次结构。
3. **方法覆盖（重写）：** 子类可以重写父类的方法，实现自己的特定逻辑。
4. **多态性：** 子类对象可以当做父类对象使用，提高代码的灵活性和可扩展性。

-  继承的语法：
在Java中，使用关键字`extends`来实现类的继承。语法如下：
`public class SubClass extends SuperClass {     // 子类的属性和方法 }`
### object类
在Java中，`Object`类是所有类的根类（Root Class），即所有类都直接或间接地继承自`Object`类。`Object`类定义了一些通用的方法，这些方法可以被所有的Java类继承和使用。以下是关于`Object`类的一些重要信息：
- `Object`类的常用方法：

1. **`equals(Object obj)`：** 用于比较两个对象是否相等。默认情况下，`equals()`方法比较的是两个对象的引用是否相同，可以根据需要在子类中重写该方法来实现自定义的相等比较逻辑。
    
2. **`hashCode()`：** 返回对象的哈希码值。哈希码值是根据对象的内存地址或者对象的属性计算得到的一个整数，用于在哈希表等数据结构中快速查找对象。
    
3. **`toString()`：** 返回对象的字符串表示。默认情况下，返回对象的类名和哈希码值的字符串表示，可以根据需要在子类中重写该方法来返回自定义的字符串表示。
    
4. **`getClass()`：** 返回对象的运行时类。可以用于获取对象所属的类的信息。
    
5. **`clone()`：** 用于创建并返回对象的一个副本。需要实现`Cloneable`接口并重写`clone()`方法才能使用。
    
6. **`finalize()`：** 该方法在对象被垃圾回收器回收之前调用。一般不建议在程序中重写`finalize()`方法，因为无法保证它会被及时调用。
7. 
## 多态
在Java中，多态（Polymorphism）是面向对象编程的三大特性之一，它允许不同类的对象对同一消息做出响应，即同一个方法调用根据对象的不同而表现出不同的行为。多态性分为编译时多态和运行时多态两种形式。
-  编译时多态（Compile-time Polymorphism）：
编译时多态也称为方法重载（Method Overloading），是指在同一个类中，可以定义多个方法具有相同的名称但参数列表不同的情况。编译器根据方法的参数列表来决定调用哪个方法。
- 运行时多态（Runtime Polymorphism）：
运行时多态也称为方法重写（Method Overriding），是指子类重写父类的方法，当通过父类引用指向子类对象并调用被重写的方法时，根据对象的实际类型来确定调用哪个方法。  
  

多态性可以提高代码的灵活性和可扩展性，使代码更容易维护和扩展。以下是多态的常见实现方法，由于[[Java笔记(一)--面向对象#^58567a|方法的重载]]在上方已经有所提及，故不再谈。
### 方法的重写
在Java中，方法的重写（Method Overriding）是指子类重新定义（覆盖）其父类中已经定义的方法，以实现子类对该方法的定制化需求。在方法重写中，子类中的方法与父类中的方法具有相同的名称、参数列表和返回类型。

-  方法重写的规则：
	1. **方法名、参数列表和返回类型必须相同：** 子类中重新定义的方法必须与父类中被重写的方法具有相同的方法名、参数列表和返回类型。
	2. **访问修饰符不能比父类中的方法更严格：** 子类中重写的方法的访问修饰符不能比父类中被重写方法的访问修饰符更严格。例如，父类中的方法为`protected`，则子类中的方法可以是`protected`或`public`，但不能是`private`。
	3. **子类方法不能抛出比父类方法更宽泛的异常：** 如果父类方法抛出了异常，子类重写的方法可以不抛出异常，或者抛出与父类方法相同的异常，但不能抛出比父类方法更宽泛的异常。

### 泛型
在Java中，泛型（Generics）是一种在编译时期进行类型检查和类型安全的机制，它允许类、接口和方法在定义时使用一个或多个类型参数（类型变量）来表示其中的数据类型。使用泛型可以使代码更加灵活、可重用，并提高代码的安全性。
#### 泛型类
使用泛型的类称为泛型类。泛型类在定义时可以指定一个或多个类型参数，这些类型参数可以在类的成员变量、方法参数、方法返回值等地方使用。
```java
public class Box<T> {
    private T data;
    
    public void setData(T data) {
        this.data = data;
    }
    
    public T getData() {
        return data;
    }
}
```
#### 泛型方法
使用泛型的方法称为泛型方法。泛型方法在定义时可以拥有自己的类型参数，与泛型类的类型参数可以不同。
```java
public <T> T printData(T data) { System.out.println(data); return data; }
```
**泛型接口（Generic Interface）：** 使用泛型的接口称为泛型接口。泛型接口可以定义一个或多个类型参数，并在接口的方法中使用这些类型参数。

`public interface List<T> {     void add(T element);     T get(int index); }`
#### 泛型的界限
在Java中，泛型的界限（Bounds）指的是限制泛型类型参数的范围，可以通过界限来指定泛型类型参数必须是某种类型或其子类型。泛型的界限有上界（Upper Bound）和下界（Lower Bound）两种。
### 上界（Upper Bound）：

上界用`extends`关键字指定，表示泛型类型参数必须是指定类型或其子类。在泛型类或泛型方法中使用上界，可以限制泛型类型参数的范围，使其只能是指定类型或其子类。
```java
public class Box<T extends Number> {     
private T data;         
public void setData(T data) {        
this.data = data;     
}          
public T getData() {        
return data;   
}
}
```
在上面的例子中，`Box`类的类型参数`T`必须是`Number`类或其子类，这样就限制了`Box`类的实例只能存储`Number`类型或其子类的数据。

### 下界（Lower Bound）：

下界用`super`关键字指定，表示泛型类型参数必须是指定类型的父类。下界通常用于限制泛型类型参数可以接受的最低类型。
```java
public void processElements(List<? super Integer> list) {    
for (Object element : list) {         // 处理元素     } }
```
在上面的例子中，`processElements`方法接受一个`List`类型的参数，但这个`List`中的元素必须是`Integer`类型的父类。这样做可以确保在处理元素时，元素的类型至少是`Integer`类型。

### 通配符（Wildcard）：

通配符`?`可以用于表示不确定的泛型类型，在泛型的界限中经常与通配符一起使用。通配符可以用于指定泛型类型参数的上界或下界。

```java
public void printList(List<? extends Shape> shapes) {   
for (Shape shape : shapes) {  
System.out.println(shape);   
}
}
```

在上面的例子中，`printList`方法接受一个`List`类型的参数，这个`List`中的元素必须是`Shape`类或其子类。这样就可以确保在方法中处理的元素都是`Shape`类型或其子类。

通过使用泛型的界限，可以提高代码的类型安全性，同时限制泛型类型参数的范围，使代码更加健壮和可靠。
#### 类型擦除
在Java中，泛型是通过类型擦除（Type Erasure）来实现的。类型擦除是Java泛型的一种实现方式，它在编译时期会将泛型类型信息擦除，将泛型类型参数替换为它们的边界或者Object类型。这样做是为了保持与之前版本的Java代码的兼容性，并且可以在运行时节省内存。
- 类型擦除的过程：

	1. **擦除泛型类型参数：** 在编译时，所有的泛型类型参数都会被擦除，替换为它们的边界类型或Object类型。例如，`List<T>`会被擦除为`List<Object>`。
	2. **擦除泛型方法：** 泛型方法的类型参数也会被擦除，方法中的泛型类型会被替换为其边界类型或Object类型。
	3. **擦除泛型边界：** 如果泛型类型参数有边界限制，边界限制也会被擦除。例如，`<T extends Number>`会被擦除为`<Number>`。
    

- 类型擦除的影响：
	1. **无法获取泛型类型参数的具体类型：** 在运行时，无法获取泛型类型参数的具体类型信息，因为类型信息在编译时已被擦除。例如，无法通过`instanceof`来判断泛型类型。
	2. **泛型类型参数被替换为Object类型：** 擦除后，泛型类型参数会被替换为Object类型，这可能导致需要进行强制类型转换。
	3. **原始类型（Raw Type）：** 在擦除后，泛型类会有一个对应的原始类型，原始类型是没有指定泛型类型参数的泛型类。例如，`List<T>`的原始类型是`List`。
	4. **警告信息：** 使用未经检查的操作会导致编译器生成警告信息，因为编译器无法检查泛型类型参数的具体类型。

尽管类型擦除会带来一些限制和不便，但它是Java泛型实现的一种折中方案，可以保持与之前版本的Java代码的兼容性，并且在运行时节省内存。开发者在使用泛型时需要留意类型擦除带来的影响，以确保代码的正确性和可靠性。
### 抽象类
在Java中，抽象类（Abstract Class）是一种不能被实例化的类，通常用于定义具体类的通用属性和方法，以及规范子类必须实现的方法。抽象类可以包含抽象方法（没有方法体的方法）和非抽象方法（有方法体的方法）。
- 特点：
	1. **不能被实例化：** 抽象类不能直接实例化，只能被用作其他类的父类。
	2. **可以包含抽象方法：** 抽象类中可以包含抽象方法，子类必须实现这些抽象方法。
	3. **可以包含非抽象方法：** 抽象类中可以包含非抽象方法，子类可以直接继承或重写这些方法。
    
-  定义抽象类：
	使用`abstract`关键字来定义抽象类，示例代码如下：
	
```java
public abstract class Shape {          
// 抽象方法
public abstract double calculateArea();         
// 非抽象方法     
public void printDescription() {         
System.out.println("This is a shape.");     
	}
}
//在上面的示例中，`Shape`类是一个抽象类，包含一个抽象方法`calculateArea`和一个非抽象方法`printDescription`。
```

### 继承抽象类：
子类继承抽象类时，必须实现抽象类中的所有抽象方法，除非子类也是一个抽象类。

```java
public class Circle extends Shape {       
private double radius;         
public Circle(double radius) {      
this.radius = radius;     }         
@Override    
public double calculateArea() {   
return Math.PI * radius * radius;     
	} 
}
//在上面的示例中，`Circle`类继承了`Shape`抽象类，并实现了其中的抽象方法`calculateArea`。
```
### 接口
在Java中，接口（Interface）是一种抽象类型，用于定义类应该遵循的行为。接口中只包含常量和抽象方法，没有实例变量和具体方法。类可以实现一个或多个接口，从而实现接口定义的方法。
-  特点：
	1. **接口中的方法都是抽象方法：** 接口中的方法默认为`public abstract`，不包含方法体。类实现接口时必须实现接口中定义的所有方法。
	2. **接口中的变量默认为常量：** 接口中的变量默认为`public static final`，必须被初始化。
	3. **类实现接口：** 类可以通过`implements`关键字实现一个或多个接口，实现接口中定义的方法。
-  定义接口：
使用`interface`关键字来定义接口，示例代码如下：
```java
public interface Animal {  
// 接口中的常量    
int LEGS = 4;        
// 接口中的抽象方法   
void eat();         
void sleep();
}
//在上面的示例中，`Animal`接口定义了一个常量`LEGS`和两个抽象方法`eat`和`sleep`。
```
- 实现接口：
类通过`implements`关键字来实现接口，示例代码如下：

```java
public class Dog implements Animal {          
@Override
public void eat() {        
System.out.println("Dog is eating.");    
}         
@Override    
public void sleep() {    
System.out.println("Dog is sleeping.");     
	}
}
//在上面的示例中，`Dog`类实现了`Animal`接口，并重写了接口中定义的`eat`和`sleep`方法。
```
- 总结：
	- 接口是一种抽象类型，定义了类应该遵循的行为。
	- 接口中只包含常量和抽象方法，不包含实例变量和具体方法。
	- 类通过`implements`关键字实现接口，并实现接口中定义的方法。
	- 接口提供了多重继承的能力，规范了类的行为，降低了耦合度，提高了代码的灵活性和复用性。
### 克隆
在Java中，对象的克隆是指创建一个现有对象的副本，使得两个对象在内存中具有相同的状态，但是在堆内存中拥有不同的内存地址。Java中对象的克隆可以通过实现`Cloneable`接口和重写`clone()`方法来实现。
- 浅拷贝（Shallow Copy）：
	浅拷贝是指只复制对象本身和对象中的基本数据类型字段，而不复制对象中的引用类型字段。如果对象中包含引用类型字段，则浅拷贝后的对象和原对象会共享引用类型字段指向的对象。
- 深拷贝（Deep Copy）：
	深拷贝是指复制对象本身以及对象中的所有引用类型字段，包括引用类型字段指向的对象，从而创建一个完全独立的对象副本。


- 实现对象克隆：
	1. **实现`Cloneable`接口：** 需要克隆的类必须实现`Cloneable`接口，该接口是一个标记接口，没有任何方法，只是用来标识该类可以被克隆。
	2. **重写`clone()`方法：** 在需要克隆的类中重写`clone()`方法，调用`super.clone()`方法进行浅拷贝，如果需要实现深拷贝，则需要在`clone()`方法中对引用类型字段进行深度复制。
# 异常机制

## 异常类型
在Java中，异常（Exception）是程序在运行过程中出现的意外情况，可以分为两种类型：检查异常（Checked Exception）和非检查异常（Unchecked Exception）。
### 检查型异常
 **检查异常（Checked Exception）：** 是在编译时期必须进行处理的异常，必须通过`try-catch`块或者在方法签名中使用`throws`关键字进行处理。例如：`IOException`、`SQLException`等。
### 非检查型异常
**运行时异常（Unchecked Exception）：** 是在运行时期可能会出现的异常，可以选择处理也可以不处理，不强制要求使用`try-catch`块或者`throws`关键字。例如：`NullPointerException`、`ArrayIndexOutOfBoundsException`等。
### 错误
在Java中，错误（Error）通常表示严重的问题，通常是由于系统级问题导致的，而不是由程序本身的错误引起的。与异常不同，错误通常是无法被程序本身处理或恢复的，因此通常不需要捕获或处理。

常见的Java错误包括但不限于：

1. **虚拟机错误（Virtual Machine Error）：** 如`OutOfMemoryError`（内存不足）、`StackOverflowError`（栈溢出）等，通常表示虚拟机运行时遇到严重问题。
2. **线程错误（Thread Error）：** 如`ThreadDeath`（线程中止）等，通常表示线程运行时遇到严重问题。
3. **错误的子类（Error subclasses）：** Java中还有一些其他错误的子类，如`AssertionError`（断言错误）、`NoClassDefFoundError`（找不到类定义错误）等。

与异常不同，错误通常表示程序无法继续运行，因此通常不需要进行捕获和处理。一般来说，程序员不需要专门处理错误，而是让程序自然地终止，然后通过日志等方式记录错误信息以便排查问题。
## 异常的处理
在Java中，异常（Exception）是程序在运行过程中出现的意外情况，可以干扰程序的正常流程。为了保证程序的稳定性和可靠性，程序员可以通过异常处理机制来捕获、处理和抛出异常。
### 抛出异常
在Java中，可以通过使用`throw`关键字来手动抛出异常。通过手动抛出异常，程序员可以在特定条件下引发异常，从而通知调用者或上层代码发生了异常情况。

要手动抛出异常，可以按照以下步骤进行：

1. 创建异常对象：首先，需要创建一个异常对象，可以是Java内置的异常类，也可以是自定义的异常类。
    
2. 使用`throw`关键字抛出异常：使用`throw`关键字后面跟随要抛出的异常对象来抛出异常。

需要注意的是，手动抛出异常通常用于在特定条件下通知调用者某种异常情况，程序员应该根据实际情况谨慎使用手动抛出异常，避免滥用导致代码难以维护。
### try-catch处理
在Java中，`try-catch`是异常处理机制的一种重要方式，用于捕获和处理可能发生的异常。通过使用`try-catch`块，程序可以在`try`块中尝试执行可能引发异常的代码，然后在异常发生时通过`catch`块捕获并处理异常。
## 自定义异常
在Java中，我们可以通过创建自定义异常类来实现自定义异常。自定义异常类通常继承自Java中的`Exception`类或其子类，例如`RuntimeException`。通过自定义异常类，可以根据特定需求定义自己的异常类型，并在程序中抛出和捕获这些异常。
## 断言表达式(目前不学呢)



