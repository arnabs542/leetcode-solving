# 破坏回文串

## 思路

### 暴力

用`O(26N)`枚举所有邻居，再用`O(N)`构造邻居、并判断是否回文。时间为`O(N^2)`，耗时较多。

### 贪心

从回文串修改一个字符使之变为非回文串，有两种情况：

- 特殊情况：奇回文串中，不能修改中间字符（因为无论如何修改中间字符，最终还是一个回文串）
- 一般情况：某位上的字符需要修改成不同的字符（否则还是个回文串）

再考虑最小字典序，算法为：

1. 把第一个“非a”字符修改为`a`
1. 如果原串中全都是`a`，那么为了修改，将最后一个字符修改为`b`

时间为`O(N)`。另外，还要考虑一个边界情况：当原串长度为1时，无论如何修改都不能变成非回文串。
