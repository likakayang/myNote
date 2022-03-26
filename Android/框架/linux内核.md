基于linux2.6内核，包含的主要功能有安全、内存管理、进程管理、网络协议栈、硬件驱动等。

#### 提供给Android平台的设备驱动，如下：  
-Android Binder。一个基于OpenBinder框架的驱动，对进程间通信提供支持。  
-Android电源管理。基于标准Linux电源管理系统的轻量级Android电源管理驱动。  
-低内存管理器。Low Memory Killer，可以根据需要杀死进程为其他进程释放资源。  
-匿名共享内存。Anonymous Shared MEMory Ashmem，提供大块可共享内存，还为内存提供回收和管理这些内存的机制。  
-Android PMEM。用于向用户提供连续的物理内存区域。因为DSP和某些设备只能工作在连续的物理内存上。  
-Android Logger。日志。  
-Android Alarm。设备睡眠时也会提供有一个运行的时钟。  
-USB Gadget。一个基于标准Linux USB gadget驱动框架的设备驱动。  
-Android Ram Console and Log Device。调试信息可以被写入一个被称为RAM Console的设备中。  
-Android timed device。定时控制功能。  
-Android Debug Bridge。ADB


#### 相关Libraries  
Bionic System C Library  
Media Libraries  
Surface Manage  
LibWebCore  
SGL  
3DLibraries  
Free Type  
SQLite  
SSL  
compose外部渲染，数据驱动

IPC（Inter-process Communication）  
进程间通信，指运行在不同进程的若干线程间的数据交换。  

UDS（UNIX Domain Socket）  
专门针对单机内的进程间通信，也被称为IPC Socket。

2.2之前GUI架构使用Binder，后来使用UDS。  

管程（Monitor）是可以被多个进程/线程安全访问的对象或模块。
管程中的方法都是受mutual exclussion保护的，同一时刻只允许有一个访问者使用它们。  

信号量S与PV原语操作    
信号量指共享资源的可用数量，P减小S计数，V增加S计数。   

Android中的Mutex是对pthread提供的API再封装。  
Condition条件互斥  
Barrier是具体的Condition，专为SurfaceFlinger设计，有3个接口函数wait(),open()和close()  

dalvik.vm.heapsize  
进程申请的heap空间超过系统的阈值，就会引发OutOfMemory（OOM）。  
Logcat  
Memory Monitor  
Heap View 



