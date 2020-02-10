# 933. 最近的请求次数

## 思路

- 二分查找：因为时间戳是非降序的，所以可以维护关于时间戳的有序数组，每次插入新元素的同时进行二分查找。
  - 优点：查找只需要`O(logN)`，很快
  - 缺点：空间需要`O(N)`，如果ping的次数很多、即N很大时，无法优化
- 队列：维护一个队列，队列中只保存可能有用的时间戳。当一个新的时间戳`t`到来，就把`t - 3000`之前的所有元素移除掉。
  - 优点：空间需要`O(M) <= O(3000)`，不会无限增长
  - 缺点：虽然删除头部操作只需要`O(1)`，但可能需要删除多个头部