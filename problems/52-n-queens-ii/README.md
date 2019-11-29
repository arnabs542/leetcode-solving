# 52. N皇后 II

## 思路

求所有可行解变成求可行解的数量，正常的套路是由回溯变为动态规划。然而棋盘无法状态化（难以哈希成基本类型，就算强行哈希，也很耗时、并且重叠子问题不多，代价甚至比不缓存还要大），所以还是只能用回溯来做。

另外，打表法才是最骚的。