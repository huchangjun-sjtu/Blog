# 计算机速成课笔记
本笔记参考视频来源为[【计算机科学速成课】[40集全/精校] - Crash Course Computer Science】]( https://www.bilibili.com/video/BV1EW411u7th/)

## P2 电子计算机 - Electronic Computing

### 机械继电器时代

#### 哈弗马克一号 Harvard Mark I

最大的机电计算机之一，由IBM在1944年为二战同盟国建造，包含有76万5千个组件组成

其“大脑”是“机械继电器，也即使用控制线路的电流来控制工作电路的通断，由此可用以控制如马达旋转拨动齿轮等类似操作。
![机械继电器](https://cdn.jsdelivr.net/gh/huchangjun-sjtu/picbed/image/20240113172705.png)

但由于其为机械结构，存在以下弊端：

* 速度慢：由于机械结构需要移动，切换通断速度有限，因此计算速度有限：加减法：1/3秒，乘法：6秒，除法：15秒；三角函数等1分钟+；
* 齿轮磨损：随使用而磨损，变得不可靠
* 故障率高：其约有3500个继电器，数量大，故障率高

**PS:** "BUG"一词的由来就是在Harvard Mark II 的故障继电器中发现小飞虫。

### 电子管时代

#### 热电子管 Thermionic Valve

1904年，英国 John Ambrose Fleming 发明热电子管 (Thermionic Valve)，将两个电极装在一真空气密灯泡中，其一可以加热而热电子发射(Thermionic Emission),另一电极在带**正电**时可以吸引电子形成电流。

#### 二极管 Diode

1906年，