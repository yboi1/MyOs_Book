第七章 (中断):
    1. 实现了中断向量表idt 产生异常后会提示异常号, 根据异常号可以定位错误处
    主要是通过完善了loader中, 将处理异常的地址放到table中,通过kernel.S调用实现中断处理
    2. 实现了可编程计数器 timer 通过内联汇编产生时钟中断
    3. io.h 用于操作硬盘或者显卡, 对端口进行读写
    4. init 实现中断表的初始化
    5. global   将idt中断描述符封装为宏 

第八章 (内存管理系统): 
    添加文件    (debug, memory, bitmap, string)
    1. MakeFile编写 实现项目的一键编译, 摆脱了sh文件的依赖, 想要用cmakefile配合clangd使用, 但是cmakefile报错无法找到头文件, 不知道什么原因
    2. 实现ASSERT c 语言中常常使用ASSERT, 但本质就是一个if判断而已, 调用了自己的debug函数, 实现对错误信息的打印, 方便了调试
    3. 实现string函数 编写自己的string库, 方便了对字符串的处理 
    4. 实现bitmap数据结构, 本章主要作用是为了服务内存是否使用, 通过scan和set函数可以实现对位图操作,表示内存是否被占用 及 标记为 已占用 (因为遍历内存的变量写错,debug了半天)
    5. 实现memory函数   本质就是实现了malloc, 传入页表数即可返回分配好的地址 主要涉及的操作是得到虚拟内存地址和物理内存地址, 并将两个地址映射 实现虚拟内存管理, 于前面的机制相匹配