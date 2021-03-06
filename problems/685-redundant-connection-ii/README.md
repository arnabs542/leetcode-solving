# 685. 冗余连接II

## 题意

题意不变，图由无向图变为有向图。

## 思路

### 拓扑排序法找环

无向图变为有向图后，“找环”的思路已经不适用了，因为无向图中的环，在有向图中不一定是环。比如：

```text
[ [1,2], [2,3], [1,3] ]
```

这不是环，但也破坏了树结构。所以“拓扑排序”法在这道题用不上。

### 最小生成树

一个合法的树中：

- 根：没有父结点，即入度为0
- 非根：有且只有1个父结点，即入度为1

那么多余的那条边加入了这个树后，会造成2种不同的后果（可以画图，举例验证）：

- 后继结点为根：
  - 例子：[1=>2, 2=>3, 2=>4, 3=>1]
  - 说明：所有结点的入度都为1。非根到根有路径了，产生环
  - 策略：因为这里没有根的概念了，所以可以发现：<u>移除环上的任意一条边</u>都能变成树。所以一遍Kruskal就能检测出多余的边。
- 后继结点为非根：有且只有1个结点的入度为2，但又细分为2种情况：
  - 产生环：
    - 例子：[1=>2, 2=>3, 3=>4, 4=>2]
    - 策略：<u>可移除边只有1个，即环上以入度为2的结点为后继结点的那条边</u>
  - 非环，多了一条路径：
    - 例子：[1=>2, 2=>3, 3=>4, 2=>4]
    - 策略：<u>可移除边有2个，即以入度为2的结点为后继结点的那2条边</u>

实际编码中，可以对3种情况进行讨论，也可以分2种。

## 反思总结

Kruskal算法是针对【无向】图的最小生成树算法，在有向图中却也能巧用。
