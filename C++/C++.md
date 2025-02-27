# C++

​	作为与java类似的面向对象的编程语言，两者有很多共同之处，因此，在很多方面可以类比来学习，顺便巩固复习java知识点。

## 1. C++ 简介

​	C++语言是C编程语言的直接后代，具有类型检查，面向对象编程，异常处理等附加功能（相交于C语言来说），而java具有与C++同样类似的功能。

​	C++是一种通用语言，这个通用语言是指它可以用于开发各种领域的应用程序。

## 2. C++特点

1. 更好的内存管理

   - C语言实现动态内存管理使用malloc函数或者relloc函数等等，比较麻烦
   - 而C++以及与之相似的java语言均是使用更为方便且简单的new和delete语句。

2. 面向对象

   C++和java均是支持面向对象的编程功能。这意味着在C++或者java程序中，我们可以使用流行的OPPs的概念，例如类、抽象、继承、封装以及多态等。

3. 可移植

4. 结构化编程

5. 异常处理

## 3. C++中的数据类型

​	数据类型定义了变量可以保存的数据类型，例如，整数变量可以保存整数数据，字符类型变量可以保存字符数据。

​	C++中的数据类型可以分为三组：内置、**用户定义**和**派生**。

- 内置数据类型：包括char、int、float、double、bool、

- 用户定义的数据类型

  ​	类似于C语言，C++中有三种用户定义的数据类型：

  ​		1.结构体

  ​		2.联合

  ​		3.枚举

- 派生数据类型

  ​	在C++中，我们有三种类型的派生定义数据类型：

  ​		1.数组

  ​		2.功能

  ​		3.指针

## 4. C++中的函数

​	与java类似，C++函数也可以使用函数的默认参数。在声明的时候使用默认参数。

## 5. 输入

​	对于字符串的输入：

```c++
char[20] book;
// 使用以下方法，会遇见空字符即结束输入
std::cin>>book;
// 使用cin.get功能，可以读取整行内容
std::cin.get(book. 20);
```

​	但是以上固定了数组的大小，并不是最优的方法读取字符串，为解决这个问题，C++提出了String对象，类似于Java。以下是一个示例代码：

```c++
#include <iostream>
using namespace std;
int main (void) {
    // This is how we create String object
    string str;
    cout<<"Enter a String:";
    // And this is how we get the user input
    getline(cin, str);
    cout<<"You entered: ";
    cout<<str<<endl;
    
    // push_back is used to add a character at the end of the string
    str.push_back('a');
    // pop_back is used to delete the last character of the string
    str.pop_back();
    return 0;
}
```



## 6.  C++中的指针

### 6.1 普通指针

​	与Java不同，C++保存了指针的用法。与C语言用法类似。同样，&表示取地址运算，*表示访问地址中的值。

### 6.2 this指针

​	**this**指针保存当前对象的地址，简单来说，this指针就是指向类的当前对象。

​	以下是一个代码示例：

```c++
#include<iostream>
using namespace std;
class Demo {
    private:
		int num;
    	char ch;
    public:
		void setMyValues (int num, char ch) {
            // 以下的this指针就是实例化后的对象的位置，使用->即可访问该对象
            this->num = num;
            this->ch = ch;
        }
    	void displayMyValues (void) {
            cout<<num<<endl;
            cout<<ch;
	}
};
int main (void) {
    Demo obj;
    obj.setMyValues(100, 'A');
    obj.displayMyValues();
    return 0;
}
```

​	第二种用法是使用this指针返回当前对象的引用，以便可以链接函数调用，这样就可以一次性调用当前对象的所有函数。用法如下：

```c++
#include <iostream>
using namespace std;
class Demo {
private:
  int num;
  char ch;
public:
  Demo &setNum(int num){
    this->num =num;
    return *this;
  }
  Demo &setCh(char ch){
    this->num++;
    this->ch =ch;
    return *this;
  }
  void displayMyValues(){
    cout<<num<<endl;
    cout<<ch;
  }
};
int main(){
  Demo obj;
  //Chaining calls
  obj.setNum(100).setCh('A');
  obj.displayMyValues();
  return 0;
}
```

## 7. C++中的OPP概念（重点）

### 7.1 简单介绍

​	**面向对象编程**是一种通过使用对象将复杂问题分解为更小的问题来解决复杂问题的方法。OOP就是创建可以交互的的对象，这使得在OOP中开发程序变得更加容易。

### 7.2 面向对象编程（OOP）

​	在面向对象编程中，我们使用和利用OOP功能（如**抽象**、**封装**、**继承**和**多态性**）的类和对象编写程序。

#### 7.2.1 类和对象

​	类就像数据成员和函数的蓝图，而对象是类的一个实例。

#### 7.2.2 抽象化

​	**抽象**是对用户隐藏不想管细节的过程。用户是在乎实现的结果，对于动作的过程，程序会对用户隐藏，因此类会向外部提供一些公有(public)的方法，对类的一些属性进行操作，而具体的操作细节以及属性用户并不能访问或说没有必要理解。

#### 7.2.3 封装

​	**封装**是将数据和功能组合成一个单元的过程。其实就是类的一个形成，类中会有类的一些属性以及对属性的一些操作（或称方法），

​	**封装的目的**是为了避免来自类外部对私有数据成员的访问。与java不太相似的是，c++一般的实现选择是将类的所有数据成员设为私有并创建公共函数，使用这些方法我们可以对类的私有数据成员进行访问以及进行修改。

#### 7.2.4 继承

​	**继承**是子类的对象获取父类属性的功能。在子类从父类继承属性和方法时，继承的类型会影响子类对父类成员的访问权限。以下是三种继承方法：

1. 公有继承

   - 父类的公有成员在子类中保持公有成员
   - 父类保护成员在子类中保持保护成员
   - 父类的私有成员不能在子类中直接访问

2. 保护继承

   - 父类的公有成员在子类中变为保护成员
   - 父类的保护成员在子类中保持保护成员
   - 父类的私有成员仍然无法直接访问

3. 私有继承

   - 父类的公有成员在子类中变为私有成员
   - 父类的保护成员在子类中变为私有成员
   - 父类的私有成员在子类中无法直接访问

   以下是继承的一个用法示例

   ```c++
   class Base {
       public:
   		int publicMethod() {return 1;}
       private:
   		int privateMethod() {return 2;}
       protected:
   		int protectedMethod() {return 3;}
   };
   
   class child : public Base {
       public:
   		int testPublic() {
               return publicMethod();
   	}
       int testProtected() {
           return protectedMethod();
       }
       // 不能直接继承父类的私有方法
   };
   
   int main () {
   	child d;
       d.testPublic(); // 正常运行
       // d.testProtected(); // 错误，在类外部无法访问保护乘员
   }
   ```

   

#### 7.2.5 多态性

​	**多态性**是一种功能，对象使用该功能在不同情况下表现不同。

​	在**函数重载**中，我们可以有多个名称相同但参数的数字、类型和序列不同的函数。

​	**多态性示例**：

```c++
#include <iostream>
using namespace std;
class Sum {
    public:
		int add (int num1, int num2) {
            return num1 + num2;
		}
    	int add (int num1, int num2, int num3) {
            return num1 + num2 + num3;
        }
};

int main (void) {
    Sum obj;
    
    cout<<obj.add(10, 20, 30)<<endl;
    cout<<obj.add)(9. 20)<<endl;
    
    return 0;
}
```

## 8. C++中的构造函数

​	构造函数（Constructor）是类的特殊成员函数，用于初始化类的对象，构造函数与类的名称相同，并且没有返回类型。

### 8.1  构造函数的简单示例

```c++
class hello {
	public:
		int num; 
    	char ch;
    hello () {
        num = 10;
        ch = 'a';
	}
};
```

### 8.2 构造函数VS普通成员函数（不同）

- 构造函数并没有返回类型，而成员函数必须有返回类型。
- 当我们创建类的对象时，会自动调用Constructor，而成员函数需要使用对象来访问。
- 当类没有构造函数时，c++编译器会生成一个默认的构造函数并插入我们的代码中。

### 8.3 构造函数的类型

1. 默认构造函数

   默认构造函数没有任何参数。

2. 参数化构造函数

   **带参数**的构造函数称之为构造函数，这种类型的构造函数允许我们在创建对象时传递参数。

   示例如下：

   ```c++
   class ADD {
       public:
       	ADD (int num1, int num2) {
               cout<<(num1+num2)<<endl;
           }
   };
   ```

## 9. 析构函数

​	析构函数是一种特殊的成员函数，其工作目的与构造函数正好相反，它是用于销毁（或删除）对象。

### 9.1 析构函数语法

```c++
~class_name () {
    
}
```

​	说明：与构造函数类似，析构函数名称应该与类名称完全匹配，并且析构函数声明应该始终以~符号开头。

### 9.2 调用析构函数时机

​	在以下情况下自动调用析构函数

1. 程序完成执行时
2. 当包含局部变量的作用域结束时
3. 调用delete语句时

### 9.3 析构函数规则

1. 名称应该以~开头，并且与类名相匹配
2. 一个类中不能有多个析构函数
3. 与可以有参数的构造函数不同，析构函数不允许有参数
4. 没有任何返回类型
5. 与构造函数类似，析构函数如果在类中未指定时，编译器会生成默认析构函数并插入到代码中。

## 10. c++中的结构

​	与c语言的结构struct类似，就不再赘述。

## 11. 三种数据成员

在C++中，公有成员（public）、私有成员（private）和保护成员（protected）是访问修饰符，它们用于定义类成员的访问级别。以下是这些访问修饰符的区别：

1. **公有成员（public）**：

   - 公有成员可以被类的对象直接访问。
   - 公有成员也可以被类的成员函数和非成员函数访问。
   - 公有成员通常用于定义类的接口，即对象与外部世界交互的方式。

   示例：

   ```c++
   class MyClass {
   public:
       int publicVar;
       void publicMethod() {}
   };
   MyClass obj;
   obj.publicVar = 10; // 直接访问公有成员
   obj.publicMethod(); // 直接调用公有成员函数
   ```

2. **私有成员（private）**：

   - 私有成员只能被类的成员函数访问，不能被类的对象直接访问。
   - 私有成员也不能被类的派生类直接访问。
   - 私有成员通常用于隐藏类的内部实现细节。

   示例：

   ```c++
   class MyClass {
   private:
       int privateVar;
       void privateMethod() {}
   public:
       void publicMethod() {
           privateVar = 20; // 在类的成员函数中访问私有成员
           privateMethod();  // 在类的成员函数中调用私有成员函数
       }
   };
   MyClass obj;
   // obj.privateVar = 10; // 错误：不能直接访问私有成员
   // obj.privateMethod(); // 错误：不能直接调用私有成员函数
   obj.publicMethod(); // 正确：通过公有成员函数间接访问私有成员
   ```

3. **保护成员（protected）**：

   - 保护成员与私有成员类似，它们不能被类的对象直接访问。
   - 但是，保护成员可以被类的派生类直接访问，即使是在派生类的公有或保护成员函数中。
   - 保护成员用于在继承层次中提供对派生类的访问，但仍然隐藏于外部世界。

   示例：

   ```c++
   class Base {
   protected:
       int protectedVar;
   };
   
   class Derived : public Base {
   public:
       void accessProtected() {
           protectedVar = 30; // 在派生类中直接访问保护成员
       }
   };
   Base baseObj;
   // baseObj.protectedVar = 10; // 错误：不能直接访问保护成员
   Derived derivedObj;
   derivedObj.accessProtected(); // 正确：通过派生类的公有成员函数访问保护成员
   ```

总结来说，公有成员用于接口，私有成员用于隐藏实现，保护成员用于在继承关系中保持一定的封装性。正确使用这些访问修饰符是面向对象编程中实现封装的一个重要方面。