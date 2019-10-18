# 303. 区域和检索 - 数组不可变

## 题意

给定一个不变的数组，多次询问区间值。

## 思路

因为区间查询会多次调用，并且增删改不会发生，所以可以把耗时操作全部放在初始化中。这里有2种思路：

- 暴力：遍历所有区间，求和
  - 时间：O(N^2)
- 前缀和：因为区间和就是子数组的和，所以可以使用前缀和，即构造前缀和数组
  - 时间：O(N)