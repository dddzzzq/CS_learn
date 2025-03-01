## 一、Pintos的时钟中断处理过程

1. pintos的初始化

   ​	pintos的最初的初始化是由init.c中的pintos_init函数完成，其中时钟的中断初始化由timer_init函数完成，timer_init调用了函数intr_register_ext，为中断号"0x20"注册了处理函数"timer_interrupt".

2. 时钟中断处理程序timer_interrupt

   ​	其中调用了thread_trick函数，该函数的作用是记录当前线程已经执行的时钟中断数thread_tricks，该函数定义了多少次时钟中断会引发一次调度。（>TIME_SLICE就会引发一次)，其宏定义为4.

   ​	因此当线程执行4个时钟中断后，会调用intr_yield_on_return，该函数将全局变量yield_on_return设置为true

3. 中断处理主程序intr_handler最后

   ​	在中断处理主程序intr_handler的最后，检查yield_on_return的值，如果该值为true，则引发一次thread_yield。

4. thread_yield函数处理

   ​	thread_yield所做的工作就是将当前正在执行的线程cur放入就绪队列ready_list，而后调用shedule，根据设计好的算法选择下一个要执行的线程。

5. TIME_SLICE为4，则说明每一个thread经历4个时钟中断就会将CPU让出，然后由操作系统调度下一个线程执行

## 二、pintos现有的timer_sleep函数介绍

