# 推箱子

## 思路

典型的迷宫搜索题。求最少推数，则用BFS。

一个状态需要用四维来表示：`(x, y, bx, by)`。其中`(x,y)`为人的位置，`(bx,by)`为箱子的位置。所以，`visit`标记数组是四维，而队列中的元素是5元组（额外多一个记录当前推数）。由于箱子的移动次数跟BFS层数不成正线性关系，所以需要用优先级队列来保证每次的队头是箱子移动次数最少的。

反思：推箱子问题中，如果求的是：

- 箱子的最少移动次数：优先级队列
- 人的最少步数：普通队列