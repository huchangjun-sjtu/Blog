# P8 指令和程序 - Instructions & Programs

## 意义

CPU之所以强大，正是因为其是可编程的，可以根据所需要实现各种功能。

## 举例

在上一节，通过四个简单指令，实现了从内存中取出两数相加并储存的操作。

![ADD_TWO_NUM](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240118170527.png)

本节中，引入跳转和终止等概念，构造更复杂的程序过程。

![MORE_OPCODE](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240118170927.png)

如上图新增了两数相减SUB指令，跳转JUMP指令，负条件跳转指令，终止HALT指令。

### 程序无限循环

当使用下图所示指令集进行操作时，在HALT指令前的JUMP 2指令会使得程序不停执行相加操作，而没有停止条件，会造成程序的无限循环(Infinite Loop)。

![INFINITE_LOOP](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240118171231.png)

### 带条件的循环

通过使用JUMP_NEG等条件跳转指令，可以使程序状态在满足某个条件时跳出，如下图示例中，程序取出11不停做减5的操作，直至为负数后跳出循环，并将最后非负结果输出，其实质就是11-5-5=1，实现了取余操作，使用减法实现了除法的作用。

![CONDICATION_LOOP](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240118171620.png)

## 现实应用

在前述例子中，使用了8bit的指令集，4位操作码最多有16个指令，4位地址码最多表示16个地址，显然难以承担复杂的工作。

这里的8bit称为指令长度(Instruction Length)，为了实现更加复杂的操作，最简单方法是增加指令长度，如使用32位或64位。另一种办法是使用可变指令指令，如HALT指令不需要后面的地址码可以短一些，其他带有地址码的指令则长一些，后跟表示地址的“立即值”(Immadiate Values)，直接跟在较短的操作码后面。

### Intel 4004 处理器

在1971年，Intel所发布的4004处理器就是使用了46个指令，使用了8位的操作码，以及对于使用地址码等需求，使用了8位的立即值。

![Intel 4004 OPCODE](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240118172603.png)

现代的CPU，如Intel CORE i7 有上千种指令和变种，以支持现代CPU的更多功能。
