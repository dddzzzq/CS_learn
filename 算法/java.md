# java基础知识

## 1. java程序的基本结构

***	一段Java程序（类）或者一个静态方法（函数）库，或者定义了一个数据类型。要创建静态方法库和定义数据类型，会用到下面五种语法，他们是java语言的基础，也是大多数现代语言所共有的。***

### 1.1 总述

- 原始数据类型：是计算机内部（语言内部）定义的数据，包括**整数，浮点数以及布尔值等等**，

他们的定义包括取值范围，以及对相应的值进行的操作，他们能够组合为表达式。

- 语句：声明，赋值，条件，循环，调用，返回（六种）
- 数组：多个**同种**数据类型的集合
- 静态方法：可封装以及重用代码，使得我们可以用独立的模块开发程序
- 标准输入/输出：程序与外界交换的桥梁
- 字符串：一连串字符
- 数据抽象：可以使用非原始数据类型*（下一节会学到）*

*运行java程序步骤：javac a.java (生成a.class）-> java a*

### 1.2 数组

1. 声明和创建

   格式：数据类型[] 数组名 = new 数据类型[length];

   例如：

   ```java
   // 创建一个长度为10的整型数组
   int N = 10;
   int[] num = new int[N];
   int[] num_fuben = num; // 见1.2解释
   ```

   

2. 起别名

   **数组名表示的是整个数组**

   可以理解为数组名是一个指针，指向的是数组空间。

### 1.3 静态方法（函数）

![image-20241013115356794](C:\Users\dgzsz\AppData\Roaming\Typora\typora-user-images\image-20241013115356794.png)

### 1.4 外部库

***2种不同类型的库中的静态方法***

- 系统标准库*(java.lang.\*)*
- 导入的系统库*（如Java.utils.Arrays)*：使用import

### 1.5 标准输入输出流

***主要使用StdOut以及StdIn这两个库***

- 标准输出StdOut的API

![image-20241013161455481](C:\Users\dgzsz\AppData\Roaming\Typora\typora-user-images\image-20241013161455481.png)

- 标准输入StdIn的API

![image-20241013161600396](C:\Users\dgzsz\AppData\Roaming\Typora\typora-user-images\image-20241013161600396.png)

*补充说明*：