# 287. 重复数

## 思路

`n+1`个数字中，数字范围为`1~n`，有1个数字重复多次。如果将这些数字看成链表结点，那么`nums[i]`表示结点`i`的下一个结点为`nums[i]`，链表从`0`开始，于是问题转化为求该链表的环入口。

然后算法有：

- 快慢双指针
  - 时间：O(N)
  - 空间：O(1)
- Hash
  - 时间：O(N)
  - 空间：O(N)

所以用双指针。