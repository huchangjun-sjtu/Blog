# P5 算术逻辑单元 - How computer calculate - the ALU

## 算术逻辑单元 ALU

算数逻辑单元(Arithmetic and Logic Unit, ALU)，是计算机中负责运算的组件，首个芯片封装的完整ALU是1970年发布的Intel-74181。

### 原理及组成

ALU含有2个单元，1个算数单元和1个逻辑单元。

#### 算数单元

算数单元对数字进行运算操作，最基本的操作的是将两个数相加，首先考虑将2个1bit的数字相加，其结果有四种情况，其中前三种正好与异或门XOR操作相同，而2个1相加则需要进位操作，因此引入一个加法器，来计算进位数据，如下图所示，这就构成了半加器(half adder)。

![半加器](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240115203255.png)

以上半加器可以完成2个1bit输入与2个1bit输出的计算，而为了更高bit的计算，需要在考虑2个1bit相加的基础上，考虑到低位的进位结果，因此应具有输入3个1bit，输出1个1bit的计算能力。

![全加器真值表](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240115215911.png)

为此，使用两个半加器如图串联，并将两个半加器的进位使用或门OR输出，以纳入进位项的计算。至此就构成了全加器(full adder)。

![全加器结构](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240115220604.png)

使用类似的思路，用全加器这个部件可以实现8bit与8bit数字的加法，如下所示8-bit.

![8位行波进位加法器](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240115221135.png)

不过，如果两个8-bit数据相加的结果超过了8bit，则产生了溢出(overflow)。

算数单元通常可进行，加减以及增减量(+-1)运算，对于乘除运算，则无专门电路，而是通过多次加来实现乘法等操作。这是比较便宜的处理器，节省成本的做法。复杂的有专门的乘法处理器。

#### 逻辑单元

负责AND，NOT，OR逻辑操作，和简单的数值测试，如下图所示非零检测

![非零检测单元](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116193411.png)

在以上基础上所构建的ALU可以进一步抽象为以下符号，输入输出，操作编码以及状态标识。

![ALU符号](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116193714.png)
