# 377. 组合总和4

## 题意

给定数字集合`nums`，求和为`target`的组合数，每种数字是无限的。

## 思路

我在确定题型时的脑回路是这样的：

1. 组合不是子数组、长度也不一定，所以排除`子数组`问题、`K sum`问题。
1. 如果求的是所有组合，就要用backtrack搜索了，就是[39. 组合总和(无限)](https://leetcode-cn.com/problems/combination-sum/)。
1. 但是题目设置的target可能很大，而且要求的只是组合数，所以在这里backtrack会超时，最后剩下动态规划。

OK，就是DP。然后再想想，发现这是变形的“完全背包”问题，只是结果由求最大价值变为求组合数。具体解法是：

f(n)表示和为n的组合数，则有状态转移方程：

> f(n) = f(n - C0) + f(n - C1) + ... + f(n - Cc-1)，其中Ci是指某个数字（在背包问题中，指的是代价/体积）。

如果觉得抽象，可以通过具体的例子来理解：

假如现有数字：[1,3]

- n=0时，f(0)=1，因为“啥数字都不选”也是一种方案。同时可以看到，这就是DP的初始状态。
- n=1时，因为`n=1`可以由`n=0`通过加`1`（1是可选值）来跳转，即f(1)的上一个状态有f(0)。同理，`n=1`可以由`n=-2`通过加`3`来跳转，但是f(-2)不存在，可以当成是0种方案。综上有：f(1) = f(1 - 1) + f(1 - 3) = f(0) + f(-2) = 1 + 0 = 1
- n=2时，f(2) = f(2 - 1) + f(2 - 3) = f(1) + f(-1) = 1 + 0 = 1
- n=3时，f(3) = f(3 - 1) + f(3 - 3) = f(2) + f(0) = 1 + 1 = 2
- ……以此类推

总结一下：对于每一个n（一重循环），都能通过寻找它所有的“上一个状态”（二重循环），求和之后就是f(n)。