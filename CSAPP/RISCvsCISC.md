最简单直现RISC架构优缺点的方式就是同原先的CISC架构作比较。

内存中的两数相乘

![avatar](/res/multmemory.png)

右图时当下通用计算机的存储体系结构，内存被规划为一个6行4列的空间。执行单元主管所有的计算过程。执行单元仅仅只能狗操作六个寄存器。我们现在想要（2，3）和（5，2）位置的计算结果再存储到（2，3）位置。



### CISC的方式

CISC架构旨在用尽可能少的指令来完成任务。这种实现通过让硬件处理器可以编译执行一些列复杂的指令。对于目前这个任务，一个CISC处理器选哟一个“MULT”的指令，使两个竖直加载到寄存器中，通过执行单元进行乘法操作，然后将结构存储到合适的寄存器中。这么一来，一个两数相乘的任务就可以仅通过一条指令来是想：

```assembel
MULT:2:3,5:2
```

MULT是一条复杂的指令，不需要程序员了解加载和存储的过程就可以直接操作内存中的数据。相当于一个高级语言的指令。例如，我们让a代表2：3位置的数据，b代表5：2位置的是数据。这条命令还可以这么写
$$
a=a\times b
$$
这个体系的优点是编译器只需要做很少的工作去翻译高级语言。代码长度短，仅需要非常少的RAM去存储。主要是把复杂指令写进硬件中。

### RISC的方式

RISC处理器需要使用时钟周期的精简指令。“MULT”会被分为三个操作指令。“LOAD”，将数据从存储空间移至寄存器。“PROD”，对寄存器中的操作数进行运算。“STORE”，将数据从寄存器移至存储空间。为了更清晰的表示RIRC实现的过程，用如下四条指令：

```assembly
LOAD A,2:3
LOAD B,5:2
PROD A,B
STORE 2:3,A
```

真个过程似乎更低效了，因为需要更多的指令，需要更多的RAM去存储汇编指令。编译器也需要做更多的工作是高级语言转换为这种形式。

| CISC                     | RISC                         |
| ------------------------ | ---------------------------- |
| 侧重硬件                 | 侧重软件                     |
| 复杂指令                 | 单周期的精简指令             |
| 操作内存的集成存储指令   | 操作寄存器的独立存储指令     |
| 短小的代码，高复合的周期 | 冗长的代码，低复合的周期     |
| 晶体管存储复杂指令       | 空余更多的晶体管做通用寄存器 |

然而RISC有着非常重要的优点。因为每一条指令都仅需要一个时钟周期与执行，整个执行的时间大约等同于复杂指令“MULT”的执行时间。相对于复杂指令集，RISC精简指令需要更少的晶体管空间，为通用寄存器，生出了更多的空间。整个指令集的执行时间大致相同，流水线的贷款也是可行的。

下面的公式常用来体现一个计算机的性能：
$$
\frac{time}{program}=\frac{time}{cycle}\times\frac{cycles}{instruction}\times\frac{instructions}{program}
$$
CISC致力于最小化一个程序中指令的数量，牺牲了每条指令的执行效率。RISC正相反，通过增加每个程序的指令数，从而减少每条指令的执行时间。

### RISC发展中的困顿

无论RISC有着怎样的优点，它也耗费了数十年才在商业社会中站住脚。主要是由于缺乏大量的软件环境的支持。

虽然苹果Macintosh和winNT都是兼容RISC的，win3.1和win95也都是基于RISC进行设计的。然而大多数公司不愿尝试去冒这个险。没有了商业支持，处理器开发者也不大愿意大量生产RISC芯片以使它们的价格更具竞争力。

另一个主要原因是Intel的存在。即使CISC芯片越来越难以生产，Intel也有资源慢慢挤牙膏更新新一代的芯片。即使RISC在一些领域超过的Intel，也不足以是金主们更换设备。

### RISC优点概述

  如今，Intel x86是唯一一款保留CISC架构的芯片。主要是由于计算机其他领域的进步。RAM价格发生了戏剧性的降低。在1977年，1MB的DRAM需要5000$。在1944年，同样的大小仅需要6$。编译器技术也变得更先进。所以基于RAM的RISC芯片和软件环境也变得更美好。