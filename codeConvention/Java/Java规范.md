#Java规范
---
##一、命名规范

* **Package的命名**
Package的名字应该都是由一个个小写单词组成。
```java
package com.seeyon.v3x.dee
```
* **Class的命名**
Class的名字必须由大写字母开头而其他字母都小写的单词组成，包含的所有单词都应紧靠在一起。（驼峰标识1）
```java
public class ThisAClassName{}
```
* **Class变量的命名**
变量的名字必须用一个小写字母开头，后面的单词用大写字母开头。（驼峰标示2）
```java
String userName;
String thisAClassMethod;
int userAge;
```
* **static final变量的命名**
static final 变量的名字应该都大写，并且指出完整含义。
```java
public static final String PACKAGE_CONFIG_FILE_PATH ="com.seeyon.v3x.dee";
```
* **参数的命名**
参数的名字必须和变量的命名规范一致。
* **数组的命名**
数组应该总是用下面的方式来命名：
```java
byte[] buffer;
```
而不是：
```java
byte buffer[];
```
* **方法的参数**
使用有意义的参数命名，如果可能的话，使用和要赋值的字段一样的名字
```java
public void setCounter(int size) {
    this.size = size; 
}
```
---
##二、变量定义规范
1、去掉不必要的公共变量；
2、仔细定义并明确公共变量的含义、作用、取值范围及公共变量间的关系；
3、防止局部变量与公共变量同名；
4、严禁使用未经初始化的变量，声明变量的同时对变量进行初始化；
5、编程时，要注意数据类型的强制转换；
6、当向公共变量传递数据时，要十分小心，防止赋与不合理的值或越界等现象发生。

---
##三、注释规范
###有哪些类型？
Java提供了3种注释类型
* **文档注释用“/\*\*”开始，并由”\*/”结束**
```java
/**
 * 文档注释
 */
```
* **标准注释用”/\*”开始”\*/”结束**
```java
/* 标准注释，可注释单行，也可注释多行 */
```
* **单行或行尾注释，采用”//”开始**
```java
// 单行注释
class Test {
	String name;	// 行尾注释
	int age;		// 行尾注释
}
```
###有哪些需要注意的？
* **版权信息注释**
```java
/**
 * @author zhangfb
 */
```
* **使用文档注释来描述类、接口、属性和方法**
使用Javadoc工具来生成对应的HTML格式的文档是很有好处的。Javadoc功能只认可在类、接口、属性和方法前编写的文档，会忽略方法内部的注释，并且Javadoc只认可语句前的一段注释，所以不要在语句前使用多个注释段。
```java
/**
 * add comments in class
 */
public class HelloWorld {
	/**
	 * add comments in field
	 */
	private String userName;
}
/**
 * add comments in interface
 */
public interface UserService {
	/**
	 * add comments in method
	 */
	public void reg(User user);
}
```
* **使用@Deprecated去掉已经过时的类、接口或方法**

##四、排版规范
* **程序块要采用缩进风格编写，缩进空格数为4个**
【注】：不同的IDE自动生成的代码可能不一致，根据需要，应该做相应的设置。
* **采用Java风格进行缩进（如"{"和"}"，左大括号要写在开始行的后面，右大括号要和引用它的语句左对齐）**
如下为不符合规范：
```Java
for (...)
{
... // program code
}
if (...)
{
... // program code
}
void function(...)
{
... // program code
}
```
应该书写如下：
```Java
for (...) {
... // program code
}
if (...) {
... // program code
}
void function(...) {
... // program code
}
```
* **较长的语句、表达式和参数(>120字符)要分成多行书写，长表达式要在低优先级操作符处划分新行，操作符放在新行之首，划分出的新行要进行适当的缩进，使排版整齐，语句可读。**
如下：
```Java
if (fileName != null &&
	new File(logPath + fileName).length < logConfig.getFileSize()) {
	... // program code
}
```
* **不允许把多个短语句写在一行中，即一行只能写一条语句**
如下不符合规范：
```Java
LogFileName now = null;    LogFileName other = null;
```
应写成如下：
```Java
LogFileName now = null;
LogFileName other = null;
```
* ** if、for、do、while、case、loop、switch、default等语句应独占一行，且if、for、do、while的执行语句无论多少行，都必须加{}**
如下不符合规范：
```Java
if (writeToFile) writeThread.interrupt();
```
应写成如下：
```Java
if (writeToFile) {
	writeThread.interrupt();
}
```
* ** 相对独立的程序块之间、变量说明之后必须加空行 **
如下不符合规范：
```Java
if (log.getLevel() < LogConfig.getRecordLevel()) {
	return;
}
LogWriter logWriter;
```
应写成如下：
```Java
if (log.getLevel() < LogConfig.getRecordLevel()) {
	return;
}
>
LogWriter logWriter;
```
* **对齐只能使用空格，不能使用TAB键**
为了避免不同的编辑器阅读程序时，因TAB键所设置的空格数不同而造成程序布局不整齐。例如Notepad++、UltraEdit、EditPlus、EmEditor等等。
* ** 在两个以上的关键字、变量、常量等进行对等操作时，它们之间的操作符前后都要加空格；进行非对等操作时，如果是关系密切的操作符（如.），前后不应加空格 **
【注】：采用这种松散式编程方式编写代码，目的是使代码更加清晰。
(1)、逗号、分号只在后面加空格。
```Java
int a, b, c;
for (int i=0; i<15; i++) {
... // program code
}
```
(2)、比较操作符(==,!=,>,<,>=,<=)、赋值操作符(=,+=,-=,*=)、算术操作符(+,-,*,/)、逻辑操作符(&&,||,&,|)、位操作符(<<,>>,^)等双目操作符，前后都应加空格。
```Java
if (current_time >= MAX_SQUART_TIME)
a = a + b;
a += b;
if ((a + b) > 0 && (a - b) < 5)
a = a ^ 2;
```
(3)、单目操作符(如：!、~、++、--、&地址运算符)前后都不加空格
```Java
flag = !isEmpty;
i++
```
(4)、.前后不加空格
```Java
p.id = pid;
```
(5)、if、for、while、switch等与后面的括号间应加空格，目的是使if等关键字更为突出和明显
```Java
if (a >= b && c < d)
```
* **建议类属性和方法不要交叉放置，不同存取范围的属性或者方法也尽量不要交叉放置**
```Java
类定义 {
	类的公有属性定义
	类的保护属性定义
	类的私有属性定义
	类的共有方法定义
	类的保护方法定义
	类的私有方法定义
}
```