# P7 中央处理器(CPU) - The Central Processing Unit

## 功能

CPU负责执行程序，也即各种程序所给出的指令(Instruction), 比如涉及运算的就可以调用ALU进行运算，涉及存取的就调用内存。

## 组成

* 内存：CPU运行需要一个外置的RAM用来存储指令和数据；
* 寄存器：需要一些寄存器(Register)来临时储存和操作数据；
* 指令地址寄存器：Instruction Address Register 来跟踪程序现在运行到哪一步了，储存着当前地址的内存地址；
* 指令寄存器：Instruction Register 存储的当前指令
* 时钟：Clock 以准确的信号，一定的频率推进CPU的内部操作，一般手机电脑有几千兆赫兹

![CPU组成](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117164622.png)

程序或者说指令也可以以二进制的形式储存在RAM中，如下表给出若干简单指令，一个字节中前4bit储存操作码，后4bit储存对应的RAM地址或寄存器地址。

![指令表](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117164728.png)

## 运行过程

以下从由内存取出数据，相加，再存回内存4个操作中，介绍了每个操作：取指令，解码指令，执行指令的3个阶段。

### LOAD_A 操作

#### Fetch Phase 取指令阶段（LOAD_A）

取指令阶段，根据指令地址寄存器所存地址，在RAM中取回指令00101110，并将其复制到指令寄存器中。

![LOAD_A_Fetch](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117165959.png)

#### Decode Phase 解码阶段（LOAD_A）

解码阶段，对于指令寄存器中所储存的指令，进行解码，如对应上述指令表的0010操作码，需要对前4bit进行判断确认其对应指令。

![CHECK_LOAD_A](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117170531.png)

对于后四位则将其视作相应的RAM地址。

![LOAD_A_Decode](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117170315.png)

#### Execute Phase 执行阶段（LOAD_A）

在执行阶段，根据前述解码得到的指令进行执行，如LOAD_A指令得到确认后，可开启RAM的允许读取线，根据地址取到1110（14）地址对应的数值00000011（3），并开启寄存器A的允许写入线，将该数据写入寄存器A中。

![LOAD_A_Execute](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117170749.png)

执行阶段结束后，线路关闭，并将指令地址寄存器+1，以便开启新的循环，执行阶段结束。

### LOAD_B 操作

#### Fetch Phase 取指令阶段（LOAD_B）

类似于前述操作的取指令阶段，此时指令地址寄存器为00000001（1），则在内存RAM中取回对应地址（1）的指令00011111，并复制在指令寄存器中。

![LOAD_B_Fetch](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117171826.png)

#### Decode Phase 解码阶段（LOAD_B）

类似的判断指令的前4bit操作符，并根据数据地址进行解码

![LOAD_B_Decode](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117172220.png)

#### Execute Phase 执行阶段（LOAD_B）

类似的，执行阶段根据所解码指令，从RAM中读取地址1111（15）的数据00001110，并写入寄存器B中。

![LOAD_B_Execute](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117172351.png)

执行完成后，将指令地址寄存器+1，结束本操作的执行阶段。

### ADD 操作

#### Fetch Phase 取指令阶段（ADD）

取指令阶段，根据指令地址寄存器的地址00000010（2）从RAM取出指令10000100存入指令寄存器中。

![ADD_Fetch](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117172640.png)

#### Decode Phase 解码阶段（ADD）

根据指令表对指令10000100进行解码，后四位10和00分别代表寄存器地址B和A。上述指令意思就是将寄存器B的值加到寄存器A中。

![ADD_Decode](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117175919.png)

#### Execute Phase 执行阶段（ADD）

在执行阶段，要使用ALU来进行加法操作，需要控制单元将寄存器B和寄存器A的值作为ALU的输入，并告诉ALU需要做加法操作。

ALU计算得到的输出应当存储在寄存器A中，会首先存在控制单元的隐藏寄存器中，待ALU关闭后，再写入寄存器A，以免重复相加。

![ADD_Execute](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117180243.png)

指令执行完毕后，会将指令地址寄存器+1。

### SAVE 操作

#### Fetch Phase 取指令阶段（STORE_A）

![STORE_A_Fetch](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117212036.png)

#### Decode Phase 解码阶段（STORE_A）

![STORE_A_Decode](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117212800.png)

#### Execute Phase 执行阶段（STORE_A）

![STORE_A_Execute](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240117212907.png)
