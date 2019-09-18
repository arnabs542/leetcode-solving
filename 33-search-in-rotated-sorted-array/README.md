# 33. 在旋转数组中搜索

## 题意

给定一个旋转数组，搜索目标元素，返回其下标。

## 思路

题目提示O(logN)，很明显需要用二分查找，所以思路就是：

1. 先用二分查找，找出旋转点/临界点
2. 再用二分查找，找出目标元素