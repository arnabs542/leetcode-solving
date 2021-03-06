# 69. sqrt(X)

## 思路

- 二分枚举：因为题目要求整数，所以可以在整数范围内枚举`n`，目标是找到使得`n * n <= x`的最大值，即最大化最小值（bisectRight）。关于细节，有以下几种写法：
  - bisectRight版本：最大化最小值，对应`bisectRight`
  - 左闭右开版本：因为`left = mid + 1`固定的了，表示`mid`是不可能的值，即`mid + 1`是可能的值，所以反推出条件为`(mid+1)*(mid+1)<=X`
  - 左开右闭版本：因为上面取的是`mid + 1`，其实就是“右中位数”，对应左开右闭就行
- 牛顿法（@todo 待学习……大学时学过，惭愧ing）

## 反思总结

【二分枚举】最大化最小值的模板题。
