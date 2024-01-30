# P13 算法入门 - Intro to Algorithms

## 算法

算法是指解决问题的具体步骤，不同2算法可以实现同样的功能，但其好坏可以从执行步骤的多少，占据内存的大小等方面进行评估。

## 排序

下面用一些排序算法的例子来介绍算法，

### 选择排序 Selection Sort

逐轮遍历最小值，并将最小值放到前面，其复杂度为$O(N^2)$

![Selection_Sort](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240126232254.png)

### 归并排序 Merge Sort

将整组数据，逐级二分，逐个小组内比较大小后，逐个合并为整组，其复杂度为$O(n*log(N))$

## 图搜索 Graph Search

图是由线连接起来的一堆节点，以下思考最小成本路线问题，如图所示节点代表城市，线段代表成本，寻找凛冬城到高庭最短路径。

![Graph](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240128004431.png)

### 暴力搜索

可以遍历每条可能的路径，排序比较最小成本，时间复杂度为$O(n!)$

### Dijkstra算法

是由理论计算机科学伟人Edsger Dijkstra发明的，算法复杂度为$O(n^2)$，改进算法复杂度$O(nlogn+I)$，其中$n$为节点数，$I$为线数。

基本算法过程可简述为：

1. 从初始节点出发，计算所能到达相邻节点的最小成本
2. 从第一层相邻节点从成本从大到小出发，计算所能到达下一层节点的最小成本，并更新
3. 循环第2步，直至找到到达目标点的最小值。

![Dijkstra](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240128005250.png)
