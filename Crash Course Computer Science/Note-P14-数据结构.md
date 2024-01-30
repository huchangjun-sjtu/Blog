# P14 数据结构 - Data Structures

数据结构，即数据在内存中的储存结构，希望是结构化方便读写的，基本的数据结构举例如下：

## 数组

数组(Array)，在某些编程语言中称为列表(list)或向量(Vector)，是将多个数据连续地储存在内存的一个片段中，为了准确定位数组中的某个数据，需要下标(Index)，大部分编程语言中，下标自0开始。

```python
j = {5,3,7,21,82,4,19}
a = j[0]+j[2]
```

### 字符串

字符串(Strings)的储存类似于数组，是由字母，数字标点符号等组成的数组，在内存中，其结尾是二进制0，是字符“null”，表示字符串结尾。

```python
j = "STAN ROCKS"
```

![Strings](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240127181426.png)

### 矩阵

矩阵(Matrix)可以看做是数组的数组，在内存中也可以逐维地连续储存，在定位时则需要逐层给出下标，除了常见的二维，实际可以进行任意维度的拓展。

```python
j = {{10,15,12},{8,7,42},{18,12,7}}
```

![Matrix](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240127181706.png)

![Matrix_memory](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240127181843.png)

## 结构体

除了将相同类型的多个单变量数据存在一起，将相互有联系的多种数据存在一起的结构叫做结构体(Struct)，可以进一步将多个结构体组成数组或其他形式。

![Struct](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240127182252.png)

![Struct_memory](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240127182336.png)

## 链表

上述数据结构仅能固定大小以某些顺序地储存数据，在中间难以方便地增删数据，因此，可引进链表(Linked List)来解决这个问题。

其基本单元为节点(Node)，可包括所储存的变量(Veriable)和指针(Pointer)，指针指向下一个节点的地址，通过使用指针，链表可以实现更佳灵活地数据储存。

![Node](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240127182801.png)

![Node_memory](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240127183626.png)

链表可以方便地增删节点，实现重新排序，两端缩减分割等操作，基于此也衍生出更多复杂数据结构。

### 队列

队列(Queue)顾名思义就像排队，先进先出(First-In First-Out, FIFO)，先入队(enqueuing)的数据,先出队
(dequeuing)。

### 栈

栈(Stacks)是后进先出(Last-In First-Out)，术语为入栈(Push)和出栈(Pop)。

## 树

将链表节点的指针改为两个，可以以此构建为树(Tree)结构。

其最上层的节点叫做根节点(Root)，其后的节点叫做子节点(Children Nodes)，每个节点的上层节点叫做父节点(Parent Nodes)，最下层没有子节点的节点叫做叶节点(Leaf)，每个父节点最多有两个子节点所构成的叫做二叉树(Binary Tree)。

树的一个性质就是只从根向叶连接，没有循环。

![Tree](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240127192516.png)

## 图

如果数据可以任意链接，可以使用有多个指针的节点构成图(Graph)。
