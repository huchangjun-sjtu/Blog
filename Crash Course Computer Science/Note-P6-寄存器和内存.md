# P6 算术逻辑单元 - Registers and RAM

## RAM

随机存取存储器(Random Access Memory, RAM)，仅在有电的情况下可以保持记录数据。

### 1bit储存-锁存器

通过将OR门和AND门串联，并使用回路，可以构建以下锁存器(AND-OR Latch)

|  SET  | RESET | OUTOUT |
| :---: | :---: | :----: |
|   1   |   0   |   1    |
|   1   |   1   |   0    |
|   0   |   1   |   0    |
|   0   |   0   | 之前值 |

![AND-OR LATCH](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116195012.png)

上述电路使用SET来设置要输入的值，使用RESET来归零，不方便直接使用在电路中，在此基础上，在前面添加逻辑门，构成下图中门锁(Gated Latch)，来控制数据的写入和能否写入的状态。

![GATED LATCH](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116195718.png)

上述锁存器可以记录1bit的数据，通过使用一系列锁存器，可以实现对字节8bit的储存，称之为寄存器(Registers);

![8-BIT Register](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116200909.png)

### 寄存器

在上述使用多个锁存器来储存多位数据时，由于每位锁存器都需要一条输入一条输出，则所使用的导线数目非常庞大，如256bit需要 256输入+256输出+1允许写入=513根导线，显然这种并列的设计方式对于多位数据的存储，是存在问题的。

为此，使用矩阵形式来布置门锁锁存器，启用(写入或读取)时，要打开相应的行线和列线将其激活，

![LATCH MARTRIX](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116202753.png)

如具体可使用AND门来保证仅有行线和列线均激活时，可以对该门锁锁存器启用写入或者读取功能，再这样的前提下，所有的锁存器可以使用同一根输入/输出线来进行写入和读取，因为未被激活的锁存器无法使用，将被忽略。

![LATCH MARTRIX UNIT](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116203154.png)

在这样的设计下，仅需要使用1条输入/输出数据线+1条允许写入线+1条允许读取线+16行线+16列线 = 35根线就可以实现上述储存结构，可以极大降低线的数量和结构复杂度。

但由此引出的问题就是，如何精准定位行列交叉点，对于16x16的矩阵可以使用4bit+4bit=8bit的数据来表示行和列的位置。

**多路复用器**(multiplexer)是为了将行和列的位置数据，精确定位到相应的行和列，并进行相应处理的部件。

![multiplexer](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116204153.png)

基于上述设计可以构建256-bit内存

![256-BIT MEMORY](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116204458.png)

进一步的将8个256-bit内存并联，可以设计256-byte内存器

![256-Byte MEMORY](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116204645.png)

将其封装，就得到了一个拥有256个地址，每个地址可以读写8bit值的RAM。

![256-Byte RAM](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240116204843.png)

8位的内存地址可以储存256个地址，而32位地址可以储存千兆级别的内存地址，现代的内存相较历史上的容量大了许多，但其本质都是对小内存的一层层封装。
