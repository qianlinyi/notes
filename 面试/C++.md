# 编译内存相关

## C++ 程序编译过程

编译过程分为四个步骤：

- **编译预处理**：处理以 # 开头的文件
- **编译、优化**：将源码 .cpp 文件翻译成 .s汇编代码
- **汇编**：将汇编代码 .s 翻译成机器指令 .o 文件
- **链接**：汇编程序生成目标文件，即 .o 文件，并不会立即执行，因为可能会出现：.cpp 文件中的函数引用了另一个 .cpp 文件中定义的符号或者调用了某个库文件中的函数。那链接的目的就是将这些文件对应的目标文件连接成一个整体，从而生成可执行的程序 .exe 文件。

链接分为两种：

- **静态链接**：代码从其所在的静态链接库中拷贝到最终的可执行程序中，在该程序被执行时，这些代码会被装入到该进程的虚拟地址空间中。
- **动态链接**：代码被放到动态链接库或共享对象的某个目标文件中，链接程序只是在最终的可执行程序中记录了共享对象的名字等一些信息。在程序执行时，动态链接库的全部内容会被映射到运行时相应进行的虚拟地址的空间。

二者的优缺点：

静态链接：**浪费空间**，每个可执行程序都会有目标文件的一个副本，这样如果目标文件进行了更新操作，就需要重新进行编译链接生成可执行程序（**更新困难**）；优点就是执行的时候运行速度快，因为可执行程序具备了程序运行的所有内容。
动态链接：节省内存、更新方便，但是动态链接是在程序运行时，每次执行都需要链接，相比静态链接会有一定的性能损失。

## C++ 内存管理

C++ 内存分区：栈、堆、全局/静态存储区、常量存储区、代码区。

- **栈**：存放函数的局部变量、函数参数、返回地址等，由编译器自动分配和释放。
- **堆**：动态申请的内存空间，就是由 malloc 分配的内存块，由程序员控制它的分配和释放，如果程序执行结束还没有释放，操作系统会自动回收。
- **全局区/静态存储区**（.bss 段和 .data 段）：存放全局变量和静态变量，程序运行结束操作系统自动释放，在 C 语言中，未初始化的放在 .bss 段中，初始化的放在 .data 段中，C++ 中不再区分了。
- **常量存储区**（.data 段）：存放的是常量，不允许修改，程序运行结束自动释放。
- **代码区**（.text 段）：存放代码，不允许修改，但可以执行。编译后的二进制文件存放在这里。

说明：

- 从操作系统的本身来讲，以上存储区在内存中的分布是如下形式(从低地址到高地址)：.text 段 --> .data 段 --> .bss 段 --> 堆 --> unused --> 栈 --> env

## 栈和堆的区别

- 申请方式：栈是系统自动分配，堆是程序员主动申请。

- 申请后系统响应：分配栈空间，如果剩余空间大于申请空间则分配成功，否则分配失败栈溢出；申请堆空间，堆在内存中呈现的方式类似于链表（记录空闲地址空间的链表），在链表上寻找第一个大于申请空间的节点分配给程序，将该节点从链表中删除，大多数系统中该块空间的首地址存放的是本次分配空间的大小，便于释放，将该块空间上的剩余空间再次连接在空闲链表上。
- 栈在内存中是连续的一块空间（向低地址扩展）最大容量是系统预定好的，堆在内存中的空间（向高地址扩展）是不连续的。
- 申请效率：栈是有系统自动分配，申请效率高，但程序员无法控制；堆是由程序员主动申请，效率低，使用起来方便但是容易产生碎片。
- 存放的内容：栈中存放的是局部变量，函数的参数；堆中存放的内容由程序员控制。

## 内存泄露

**内存泄漏**：由于疏忽或错误导致的程序未能释放已经不再使用的内存。
进一步解释：

- 并非指内存从物理上消失，而是指程序在运行过程中，由于疏忽或错误而失去了对该内存的控制，从而造成了内存的浪费。

- 常指堆内存泄漏，因为堆是动态分配的，而且是用户来控制的，如果使用不当，会产生内存泄漏。

- 使用 malloc、calloc、realloc、new 等分配内存时，使用完后要调用相应的 free 或 delete 释放内存，否则这块内存就会造成内存泄漏。

- 指针重新赋值


## 怎么防止内存泄漏？内存泄漏检测工具的原理？

1. 内部封装：将内存的分配和释放封装到类中，在构造的时候申请内存，析构的时候释放内存。
2. 智能指针：智能指针是 C++ 中已经对内存泄漏封装好了一个工具，可以直接拿来使用。

检测原理：

- 当要读写内存中某个字节时，首先检查这个字节对应的 Valid-Address 表中对应的 bit。如果该 bit 显示该位置是无效位置，Memcheck 则报告读写错误。
- 内核（core）类似于一个虚拟的 CPU 环境，这样当内存中的某个字节被加载到真实的 CPU 中时，该字节在 Valid-Value 表对应的 bits 也被加载到虚拟的 CPU 环境中。一旦寄存器中的值，被用来产生内存地址，或者该值能够影响程序输出，则 Memcheck 会检查 Valid-Value 表对应的 bits，如果该值尚未初始化，则会报告使用未初始化内存错误。

## 智能指针有哪几种？智能指针的实现原理？

智能指针是为了解决动态内存分配时带来的内存泄漏以及多次释放同一块内存空间而提出的。C++11 中封装在了 \<memory> 头文件中。

C++11 中智能指针包括以下三种：

- 共享指针（shared_ptr）：资源可以被多个指针共享，使用计数机制表明资源被几个指针共享。通过 use_count() 查看资源的所有者的个数，可以通过 unique_ptr、weak_ptr 来构造，调用 release() 释放资源的所有权，计数减一，当计数减为 0 时，会自动释放内存空间，从而避免了内存泄漏。
- 独占指针（unique_ptr）：独享所有权的智能指针，资源只能被一个指针占有，该指针不能拷贝构造和赋值。但可以进行移动构造和移动赋值构造（调用 move() 函数），即一个 unique_ptr 对象赋值给另一个 unique_ptr 对象，可以通过该方法进行赋值。
- 弱指针（weak_ptr）：指向 share_ptr 指向的对象，能够解决由shared_ptr带来的循环引用问题。

智能指针的实现原理： 计数原理。

## 一个 unique_ptr 怎么赋值给另一个 unique_ptr 对象？

借助 std::move() 可以实现将一个 unique_ptr 对象赋值给另一个 unique_ptr 对象，其目的是实现所有权的转移。

# 语言对比
