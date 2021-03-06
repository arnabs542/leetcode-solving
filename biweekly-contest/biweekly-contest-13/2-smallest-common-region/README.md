# 最小公共区域

## 思路

父子、兄弟关系最适合用“树”来描述，然而输入已经用数组表达了所有关系，我们并不需要把树构建出来。无论是数组还是树，求`A`与`B`的“最小公共祖先”的方法一样：先求出`A`的祖先链（子 => 父的映射），然后再求`B`的祖先链，第一个重合的就是目标。

## 反思

联想到那题“求2个链表的第一个相交结点”，解法是一样的，然而链表题有`O(1)`空间的解法。这题当然可以沿用思路，然而因为需要建立哈希表，`O(N)`空间是必需的了。
