# 最大得分的路径数目

## 思路

动态规划。因为是二维矩阵中的DP，所以BottomUp会比TopDown更简单。`dp[i][j]`表示到达`(i,j)`的最大和，同时`s[i][j]`表示到达`(i,j)`的最大和的方案数。而3个方向的移动，就是说明了拓扑序（状态转移的方向），即有：

```c++
dp[i][j] = board[i][j] + max(dp[i+1][j+1], dp[i+1][j], dp[i][j+1]); // 右下、下、右，这3者中的最大值
// s[i][j]等于三者中等于最大值的策略数之和
```
