# 426. 将二叉搜索树转化为排序的双向链表

## 题意

给定一个二叉搜索树，将其原地修改为：有序双向循环链表。

## 思路

如果不是原地修改，可以用中序遍历将树化为数组，然后再遍历数组、将其化为链表，这样就非常简单。

而原地修改，可以把中序遍历那几种思路搬过来，比如：

- 递归
- 循环
  - Morris遍历
