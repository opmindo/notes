## c编译流程
+ 预处理(.i)
+ 编译成汇编码(.s)
+ 生成机器码 (.o)
+ 链接，生成可执行文件(exe)

## 一切都是抽象，上层屏蔽下层复杂性
指令集 > cpu
文件 > io 设备
虚拟内存 > 文件、内存
进程 > 指令、文件、虚拟内存
虚拟机  > 机器

## 并发的3个层次
1. 线程级别，多线程、进程切换
2. 指令级别，一个cpu clock执行多条指令（pipelining, superscalar processor)
3. simd, Single Instruction, Mulitple data, 一条指令处理很多数据，比如一条指令做4对float加法，多媒体处理很有用
