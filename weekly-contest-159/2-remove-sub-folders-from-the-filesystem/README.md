# 删除子文件夹

## 题意

给定一堆文件夹，筛选出母文件夹。

## 思路

题意是要筛选出所有前缀。

先对所有文件夹进行排序（字典序升序），这样保证了母文件夹总是在子文件夹之前，然后筛选母文件夹有以下几种子思路，但差不多：

- 哈希表：用HashSet存放母文件夹。对于一个新文件夹A，在HashSet中搜索A的所有前缀（有多少个`/`分段就有多少个可能的前缀），如果存在则不添加A，如果都不存在，说明A是母文件夹，将A加入集合。
- Trie：Trie树同样只存放母文件夹。对于一个新文件夹A，尝试寻找其前缀，如果能找到则不插入；否则插入A。注意该Trie树的边不再是传统的单个字母，而是一个单词，所以要用Map，而不能用数组。
- 不使用数据结构：只需要一个`prev`变量记录上一个母文件夹。这才是最简单而有效的做法，因为排序不但将母文件夹放在子文件夹之前，而且也把可能有关系的放在一起、它们是连续的，所以只需要“连续判断”即可

无论是哪种子思路，都基于排序结果，所以该题的核心解法其实是【排序】。

时间复杂度：O(NlogN + NM)，其中M为文件夹的平均层数。