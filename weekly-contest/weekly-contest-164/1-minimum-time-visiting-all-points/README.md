# 访问所有点的最小时间

## 思路

思路：贪心。为了达到最少步数，需要先走对角线方向，再走水平/竖直方向。

这样两点之间的最短路径实际上是`max(deltaX, deltaY)`。