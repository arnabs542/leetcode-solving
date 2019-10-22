# 312. 戳气球

## 思路

难度较大的DP题。思路有：

- 回溯（TLE）：每次从剩余的N个中挑一个戳爆，时间为O(N!)
- 动态规划：如果先戳破气球`i`，那么`i-1`和`i+1`变成相邻，即数组会变化，这样状态就无法表示了。所以用逆向思维（有点像后序遍历那种感觉），考虑先戳破`[l, i-1]`这一段，然后戳破`[i+1, r]`这一段，最后才戳破气球`i`，这样一来，就算数组变化了，对`i`也没有额外影响。
  - Top-down
  - Bottom-up

## 相似题目

当数组会变化，导致状态无法用可缓存的简单变量来表示时，考虑“后序遍历”。类似思路相关题目：

- [546. 移除盒子](https://leetcode-cn.com/problems/remove-boxes/)

## 参考

- [小旭讲解 LeetCode 312. Burst Balloons 回溯法 动态规划](https://www.bilibili.com/video/av45180542)