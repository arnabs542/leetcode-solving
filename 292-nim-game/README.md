# 292, Nim游戏

## 题意

拿石头的博弈游戏，每次可取1～3个石头，取完者胜利。给定石头数`n`，判断先手的“我”是否能够胜利。

## 思路

“很聪明”说明每一步都是最优解，其实这才是该题目得以“运算”的前提。不妨这样分析：

- n=[1,2,3]：因为可以拿走全部，都能赢。所以有：1 => true, 2 => true, 3 => true
- n=4：因为拿1时对方拿3，拿2对方也拿2，拿3对方拿1，无论怎么走，都是输。所以有：4 => false

以上是需要分析的情况。而更大的数字，是可以递推的：

比如当`n=5`的3种情况：

- 拿1，对方就是n=4的情况，（由于两个人的每一步都是最优解，这意味着可以沿用之前的推导）于是对方输，返回true
- 拿2，对方就是n=3，对方赢，返回false
- 拿3，对方就是n=2，对方赢，返回false

所以当`n=5`时，返回true。

无论n等于多少，只要这3种策略中，存在一个让对方是false（输），那“我”就是赢（true）。故有递推式子：

> f(n) = !f(n-1) || !f(n-2) || !f(n-3)

这就是DP的状态转移方程。可以用两种方式实现：

- Top down/记忆化搜索
- Bottom up/递推：在空间上，O(N)数组可以优化为3个变量O(1)

可以类比“斐波那契数列”。

然而，这两种方法都是超时的，因为n可能很大。所以不妨用DP打表输出结果，发现只要满足`n % 4 === 0`的数字，都是返回false，其它返回true，所以存在直接而简单的解法。

有些评论也能直接推出来答案的，也可以参考一下，这里就不详述了，只讲讲上面的思路。