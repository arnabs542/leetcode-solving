# 删除一次得到子数组最大和

## 题意

最大子数组和，允许一次删除。

## 思路

如果允许的是`K`次删除，这道题同样使用动态规划来做。而状态表示为：

- `i`: 当前遍历的元素。对于Top-down来说，它表示子数组开头下标；而对于Bottom-up来说，它表示子数组结尾下标。
- `k`: 剩余删除次数

于是写法有：

- Top-down：栈深可达`10^5`，导致栈溢出
- Bottom-up：`dp[i][k]`表示以`i`结尾、剩余`k`次删除机会的最大子数组和
  - 空间优化

最后的一个细节：由于题目规定，子数组至少含有一个元素（不能是空数组），这里提供2个办法来解决：

- DP前：提前遍历一遍数组，如果最大值`max`是非整数，那么DP结果肯定为`0`，则直接返回`max`。
- DP时：将`arr[0]`作为初始状态，然后从`i=1`开始迭代。