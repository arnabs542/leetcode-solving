# 重构 2 行二进制矩阵

## 思路

我们要做的，就是要猜出/凑出满足条件的一个矩阵。暴力回溯做的话不可能，要有一定的策略。算法为：

- `upper + lower`表示两行的总和，对`colsum`求和表示所有列的总和，如果两者不相等，直接失败。
- 按列凑，策略为：
  - 如果`colsum[i] === 2`，表示第`i`列上都是1
  - 如果`colsum[i] === 0` ，表示第`i`列上都是0
  - 只有当`colsum[i] === 1`时是不确定的，不确定1在上还是在下。把前2种情况做完后，再重新遍历所有的`1`，这次我们用贪心思想，尽量使`upper`（表示上一行要填充的`1`数量）和`lower`（表示下一行要填充的`1`数量），如果`upper >= lower`，我们填充上一行，否则填充下行。
- 凑完后，检查`upper`和`lower`是否有剩余，如果有则失败，否则成功。
