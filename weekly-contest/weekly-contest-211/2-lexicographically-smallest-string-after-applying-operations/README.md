# 5544. 执行操作后字典序最小的字符串

穷举/回溯的可行性？

- 累加：对于每一位来说，累加后的数字是循环的，那么无论a是多少、至多累加`10`次就会重复。
- 轮转：该操作也是循环的，无论b是多少、至多轮转N次（`N <= 100`）就会重复。

那么数字最多有`10 * 100`即`1000`个，完全可行。
