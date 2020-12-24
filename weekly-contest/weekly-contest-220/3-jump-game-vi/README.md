# 1696. 跳跃游戏 VI

## DP + 单调队列

思路还是很简单的：

`dp[i]`的上一个状态`dp[j]`有`k`个，这样时间会达到`O(N^2)`，会超时。

但其实我们只关注`max(dp[j])`。在遍历的过程中，这个`k区间`是一个右移的固定窗口，所以这是一个「滑动窗口中的max」问题，可以使用单调双端队列在`O(N)`时间求出。同时进行DP，整体时间也是`O(N)`。

## DP + 堆

差不多，时间为`O(NlogN)`。