# 138. 复制带随机指针的链表

## 思路

LeetCode上鲜有的【深拷贝】题目之一，与其说考察链表，倒不如说考察编程的基础知识。

深拷贝，有2种实现方式：

- 递归（本质上是树的DFS）：
  - 时间：O(N)，树深为链表长度
  - 空间：O(N)，每个递归单元为O(1)
- 迭代（本质上是树的BFS）：先处理next、同时记录旧新结点的映射，再处理random
  - 时间：O(N)，循环2次
  - 空间：O(N)，需要记录N个映射