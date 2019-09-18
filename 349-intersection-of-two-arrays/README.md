# 349. 求交集

## 题意

求两个数组的交集，并且结果集是个集合(隐含“去重”)。

## 思路

brute-force解法：遍历数组A、对于每一个元素，都到B中线性查找，所以时间是O(N * N)。

前者是遍历、无法优化。但后者由于是搜索，可以优化成以下几种：

- Hash: 总体为O(N) + O(N * 1) = O(N)
- 二分查找: 总体为O(NlogN) + O(N * logN) = O(NlogN)

另外还有一种基于有序数组的思路：

- 双指针法：利用2个指针分别遍历这2个数组，从最小开始向更大的方向推进。总体为O(NlogN) + O(N) = O(NlogN)