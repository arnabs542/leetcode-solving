# 5511. 二进制矩阵中的特殊位置

矩阵的这类题已经做了很多次了，无非两种方法：

- 暴力：`O(N^3)`
- 哈希：提取重复工作/预处理，即提前算好每一行/每一列有多少个1（和）。这样可以降低到`O(N^2)`
