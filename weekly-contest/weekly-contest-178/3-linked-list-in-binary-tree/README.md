# 1367. 二叉树中的列表

## 题意



## 思路

本质上是“判断子串”，只不过在数据结构上有变化：text变成二叉树、pattern变成链表。与字符串相比，遍历过程由迭代（下标访问）变为递归。那么理论上有两种方案：

- 暴力：树中的每个结点都可以作为起点（对齐链表头），然后遍历链表。时间为`O(NM)`。
- KMP（@todo 待探究）
