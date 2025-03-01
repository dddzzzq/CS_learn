# 中断处理的学习

## 1. 任务的描述

1. 熟悉pintos的调试方法
2. 掌握80x86中断描述符表的结构
3. 掌握Pintos的中断处理过程
4. 完成一次中断的调试

## 2. 80x86的中断以及异常处理机制

​	80x86的中断异常处理机制可以透明的处理发生的中断和异常现象（在Pintos中称为外部、内部中断）。当接收到一个异常或者中断时，处理器会自动的停止当前正在进行的线程/进程，并开始运行中断和异常处理程序。当处理程序结束后，处理器会进一步恢复执行被中断的线程/进程。

## 3. Pintos系统中断处理

### 3.1 中断初始化

​	在Pintos中threads/interrupt.c中的intr_init()**设置IDT**，其中128行`id[t] = make_intr_gate(intr_stubs[i], 0)`使得IDT的每个入口都指向threads/intr-stubs.S中定义的唯一入口点，即intrNN_stub(),再有134行执行LIDT指令，将IDTR寄存器指向设置好的IDT。其中NN是十六进制表示的中断号。intrNN_stub()的实体在intr-stubs.s文件中，共有256个函数接口。

​	intr_init()函数由pintos_init()函数(可以理解为pintos的main函数)调用，因此在启动pintos的过程中即完成了中断初始化。

## 3.2 Pintos的中断处理过程

1. pintos系统启动后自动完成中断的初始化，使得每个中断都会指向统一的唯一入口点。
2. 执行intrNN_stub()函数：CPU自动跳转到该函数入口处执行，而在执行该函数第一步之前，CPU会自动进行一些数据保存工作：*将ss、esp、eflags、cs、eip等寄存器压入到内存栈中。*而因为threads这章的实验并不存在特权级的转变，因此不会将ss和esp压入栈中。intrNN_stub()函数最重要完成的任务是将中断向量号压入栈中。
3. 然后跳转到intr_entry()函数执行，这个函数主要帮我们将CPU还没有压入栈中的寄存器值压栈，然后调用intr_handler()函数
4. 执行intr_handler()函数，这个函数在interrupt.c中定义，这个函数主要工作是调用为处理中断异常而注册的函数，即中断处理函数（如果没有对应注册函数的话，会显示一些错误）。

​	因此，pintos中断处理过程可以表示为如下的图示：

![image-20241103171256965](D:\DZQ\课程学习\图片\image-20241103171256965.png)

### 3.3 后续操作

​	当从intr_handler函数返回之后，intr-stubs.S中的38-64行汇编代码会恢复先前保存的所有CPU寄存器，并指示CPU从中断返回，这个指示由iret指令完成，这个指令还会将保存的信息恢复。

## 4. debug操作

- 设置断点：
  	break操作，例如：**`break file_name:21`**，表示在该文件的21行设置断点

- ![ef9e089d22a9e4a77e0de66fd393301](D:\Program Files (x86)\新建文件夹\WeChat Files\wxid_5um2vqpn5dth22\FileStorage\Temp\ef9e089d22a9e4a77e0de66fd393301.png)