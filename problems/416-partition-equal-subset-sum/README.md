# 416. 分割等和子集

## 题意

给定一组正整数，是否能分成和相等的两半。

## 思路

分为和相等的两个集合 => 寻找和为`sum/2`的两个集合 => 是否存在和为`sum/2`的任意组合

### Top-down DP/回溯

基本算法是：对于每一个数字，选择“取”或“不取”，然后递归到下一个数字。时间复杂度高达O(2^N)，并且N最大为200，很容易TLE。

但测试数据应该较弱，因为如果进行以下方面的优化就不会TLE：

- 回溯之前的判断：
  - 数组长度不能小于2
  - sum不能为偶数
  - 最大值不能超过`sum / 2`
- 提前进行逆序排序：先累加大的数字，可以更快地逼近目标和
- 剪枝：如果当前累计的和已经超过目标和了，则不要继续了

### Bottom-up DP/01背包问题

题目给出的“注意”中，200 * 100 = 20000，疯狂暗示我们用DP（开20000的数组不会爆，也不会超时）。

假设每个数字为物品的重量，问能否“恰好”放满容量为 sum/2 的背包。

设SUM最大为K，则有复杂度：

- 时间：O(NK)，最大为20000，不会超时
- 空间：压缩后可达O(K)

### bit操作

将每一个数字化为二进制中的位数。比如1、5这两个数字，能组成的和有：0、1、5、6：

```text
初始: 0000 0001
加入1: 0000 0011
加入5: 0110 0011
```

从位数上可以看到`0110 0011`中有0、1、5、6这4个和。所以每次加入一个数字n，相当于将当前的数位A全部左移n位变为B，然后B | A（累计）。

在C++（BitSet容器）、Python下是可行的，但在JS下因为按位操作只能用于32位之内的整数[MDN：按位操作符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators)，所以不可行。
