# P9 高级CPU设计 - Advanced CPU Designs

## 提高CPU性能的各种方法

### 提高时钟频率

从早期每秒一次到现在GHz的计算机，提高计算频率一直是提高性能的有效手段。

在早期，减少晶体管的切换时间是提速的重要方式。

### 提高CPU复杂度

如前述用减法循环代替除法计算的例子，使用大量时钟时间来进行除法运算。

因此为了缩短计算时间，在现代的ALU中已经通过硬件设计添加了除法计算功能，可以直接完成除法运算。

并且现代处理器有专门的电路来处理如图形操作，解码压缩视频，加密文档等专门操作。

指令集随着功能更新而不断新增，但为了旧指令的兼容性(Backwards Compatibility)，需要将其保留，指令集也不断扩大。

### 设置缓存Cache

快速的时钟速度导致RAM与CPU之间的缓慢数据传输成为瓶颈，RAM与CPU之间通过总线通讯，从内存读取数据的指令可能要数个时钟周期来执行。

![CACHE](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240118231259.png)

为了提高效率，在CPU中设置缓存(Cache)，从RAM取数据时，可以直接拿一批，这样可以快速在CPU中进行处理，避免了频繁存取的问题，如果想要的数据在缓存中，称之为缓存命中(cache hit)，若不在，则称之为缓存未命中(cache miss)，缓存也可以在长运算中储存中间值。

由此引发了Cache与RAM数据不同步的问题，因此在缓存中有一块空间专门储存特殊标记，称为“脏位”(Dirty Bit)，记录Cache中数据是否已经修改，如果在加载新内容腾出Cache 空间时，这部分是“脏”的，则需要先将其写回RAM。

### 指令流水线

在前述指令的运行过程中，每个式中周期只进行一个阶段，需要三个周期才能执行一个指令。

![3_clock_1_instruction](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240119100805.png)

而采用指令流水线(Intruction Pipelining)的设计，由于不同阶段使用了CPU的不同部分，因此可以在解码本次指令时，取出下次代指令，执行上次指令，来实现平均每个时钟周期完成一条指令的流水线作业。

![1_clock_1_instruction](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240119101005.png)

为了实现这个流水线，必须考虑流水线的执行指令的依赖关系，如在读取某个数据时，正在执行的指令或许会改变它，就产生了冲突，因此要搞清数据依赖性(Data Dependencies)，必要时停止流水线来保证正确。

**乱序执行**(out-of-order execution)指的是将有依赖关系的指令，进行动态排序，来最大缩短流水线停工时间。需要依靠复杂的电路实现。

**推测执行**(Speculatative execution)指在有跳转指令的情况下，不同的条件会触发不同的指令执行流，简单的流水线可能会停止并等待JUMP指令的条件值确定，而高级的流水线则为了避免延迟，采用推测执行的技巧，猜测指令跳转后的执行流，提前放入流水线，当JUMP结果确定：

* 若猜对了，可立即执行，减少延迟时间
* 若猜错了，会清空流水线(Pipeline Flush)，执行正确流水线

为了减少猜错清空的概率，现代厂商研究了复杂的“分支预测”(Branch Prediction)技术，正确率超过90%。

### 超标量处理器

超标量处理器(Superscalar)是为了进一步充分利用处理器空闲部分，研发的一次性处理多条指令的技术，对使用频率高的指令增添更多电路进行处理。

![Superscalar](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240119102538.png)

### 多核处理器

多核处理器(Multi-core Processors)是整合多个独立处理单元在同一个CPU中，由于其联系紧密，可以共享资源合作处理指令。

![QUAD_CORE](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240119102723.png)

### 超级计算机

超级计算机(Supercomputer)是为了解决怪兽级运算，所整合许多个CPU在同一台计算机，可提供强大算例。

![Supercomputer](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240119103017.png)

截止视频发布时，最大的超级计算机是中国神威太湖之光，包含40960个256核CPU，共超过1千万个核心，频率1.45GHz，每秒可进行9.3亿亿次浮点数运算。
