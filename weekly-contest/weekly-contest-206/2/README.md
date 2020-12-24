# 5512. 统计不开心的朋友

题目给定的规则比较复杂，但这恰恰说明这道题不会有什么新思路，就是个“阅读理解”。

暴力模拟的话，时间上是`O(N^3)`。但用哈希，对每个`preferences[i]`求反向映射，可以快速判断两个朋友哪个跟`i`更好，所以整体可以在`O(N^2)`完成。