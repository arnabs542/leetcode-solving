# 161. 相隔为 1 的编辑距离

## 思路

根据字符串的长度S、T分类讨论：

- S === T：看能否通过【修改】，其实就是看汉明距离是否为1
- S - 1 === T：看是否通过【删除】，比较字符串即可
- S + 1 === T：看是否通过【增加】，同样比较字符串即可