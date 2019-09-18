# 46. 全排列

## 题意

给定一个没有重复数字的序列（用数组表示），返回其所有的排列。

## 思路

可以用递归、迭代这2种方法。不过在这里2种方法对应的思路是不同的。

### 1. 递归

对于这N个数字，每次取走一个：第1次有N个选择、第2次有(N-1)种选择……直到第N次只剩下1个数字可以选择，就到了叶子结点，即一个排列。具体实现时，可以细分为2种写法：

1. 递归单元接收不同的数组（长度更改）：取走1个，数组就少1个数字，比较符合直觉，写起来也很简单。
2. 递归单元接收相同的数组（长度不变）：乍一想，需要用额外的数据结构来标记哪些数字已经被“取走”、哪些“可用”，未免太过麻烦，而且也提升了时间复杂度。所以有个巧妙的方法，就是<u>交换元素</u>：把将要取走的数字交换到最前面，即数组的前一段都是已经取走了的，后一段是可用的，然后用变量标记分隔的位置即可。

个人更喜欢第1种。

### 2. 迭代

在这里，迭代解法所用的思路，跟递归的不是同一个。反而跟[78. 子集](https://leetcode-cn.com/problems/subsets/solution/hui-su-suan-fa-by-powcai-5/)用的思路几乎一样，所以代码也差不多：

核心思路是：对于每一个即将加入的新数字，它可以插入当前序列的任意一个位置。

但是，比起递归法，迭代法有个小瑕疵，就是遍历出来的排列是“乱序”的，不符合我们通常意义上的字典序。

### 3. 位运算

@todo 这个方法很创新，了解一下。

## 反思总结

递归和迭代是一对常见CP，但不一定是同一种思路的不同实现方式。