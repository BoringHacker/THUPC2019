## 题面检查

* I 表示 INFO，W 表示 WARNING，E 表示 ERROR

### A

* I: 建议明确写出 `n` 和 `m` 的最小范围，“正整数”和“非负整数”虽然可以，但是影响阅读体验。
* 给定一棵树，和多个询问。每个询问给定 `p0, d0, p1, d1`，求所有 `d(a, b)` 的和。
* 其中 `d(p0, a) <= d0` 且 `d(p1, b) <= d1`。`d(u, v)` 表示 `u` 和 `v` 在树上简单路径的边数。
* I: 题解说可以用树分块来维护。
* I: 知识点：树分块；数据结构；这题我不会


### B

* 给定一个数据结构，和对它的 `N` 次操作。每次操作为，插入一个数，或者取出一个数（给出取出的数）。
* 问这个数据结构是否可能是 队列、栈、大根堆、小根堆。
* I: 签到题
* I: 知识点：签到题


### C

* 有个 `N * M` 的棋盘，有 `K` 个点不能走。
* 现在要从 `(1, 1)` 开始，每次可以走到当前位置的上方、右方或右上方位置。
* 问有多少种不同的方案（移动操作的序列），能够恰好（即，在最后一步）走出棋盘。
* I: `N` 不超过 1e9，`M` 不超过 1e5，`K` 不超过 20。
* I: 应该是要容斥，然后以某种方法计算答案……我不会
* I: 知识点：容斥；组合数学；这题我不会


### D

* 有个圆形的蛋糕，现在可在圆周上任取 `n` 个点，然后两两连线。问最多能将蛋糕分成多少部分。
* I: 样例有误导性很赞
* I: 考虑计算出交点数、线段（边）数，即可根据平面图的 `|V| - |E| + |F| = 2` 来求出答案。
* I: 知识点：平面图

```cpp
#include <stdio.h>

int V(int n) {
    int ret = 0;
    for (int i = 0; i <= n - 2; i++) {
        ret += i * (n - 2 - i) * n;
    }
    return ret / 4 + n;
}

int E(int n) {
    int ret = 0;
    for (int i = 0; i <= n - 2; i++) {
        ret += (i * (n - 2 - i) + 1) * n;
    }
    return ret / 2 + n;
}

int main() {
	int n;
	while (scanf("%d", &n) == 1) {
		printf("%d\n", 1 + E(n) - V(n));
	}
}
```


### E

* W: 没有给定 `n_A, n, n_B` 的范围的最小值。
* 有个凸多面体，在空间中做匀速直线运动。
* 另有一个物体，为若干个凸多面体的并。
* 现在需要求出，这两个物体的交集的大小，关于时间的（定）积分，时间的范围为 `[0, +inf)`。
* I: 将两个物体均投影到速度向量的法平面上，然后……这题我不会
* I: 知识点：三维计算几何；这题我不会


### F

* 有个 `n` 进制的数，共有 `k` 位。即，这个数有 `n^k` 种取值。
* 现在给这个数的每种取值定义一个得分。在本题中，会输入所有这些得分。
* 接下来有 `q` 次在线询问，每次给定一个数 `a`，和一个操作次数 `T`，问对 `a` 进行 `T` 次操作后，所有可能的结果（重复也算）的得分之和（模998244353）。
* 每次操作是指，将 `a` 的某一位改变为其他的值。也就是说，`T` 次操作有 `(n-1)^T k^T` 种决策。
* I: 考虑一次询问，由于操作是各向同性的，因此只需对每个 `i`，统计与 `a` 有 `i` 位不同的数的得分之和，乘上这些数的决策个数。
* I: 前者可以类似 fwt 算法进行预处理，后者可以矩乘+预处理矩阵的幂。
* I: 时间复杂度 `O(n^k k^2 + P^{0.5} k^{2.5} + q k^2)`
* I: 知识点：智商


### G

* 有个长度为 `N` 的整数序列 `S`，每次 A 和 B 轮流操作。
* A 先给出一个长度为 `N` 的正整数序列 `T`。
* B 选择一个 `x`，将 `T` 循环右移 `x` 位之后加到 `S` 上。
* 如果某一轮结束后，`S` 中的每个数都是给定的质数 `P` 的倍数，则 A 获胜。
* 问 A 是否可能在有限步内获胜，以及如果能，最少几轮可以保证获胜。
* I: 这题我不会
* I: 知识点：这题我不会

### H

* 题面4页的大模拟；略
* I: 知识点：大模拟

### I

* I: “快速地略过了题目描述” -> “掠过”？？
* E: 没有说明输出保留的小数位数，以及答案比较的方式
* 有 `n` 个绝对值一次函数（`f(x) = |a_i x + b_i|`），求这些函数的每个前缀和的全局最小值。
* `1 <= n <= 5e5, |a_i|, |b_i| < 1e5`
* I: 只会分块的做法啊，`5e5*sqrt(1e5)` 显然跑不过
* I: 知识点：数据结构

### J

* W: 请在题目描述里加一句，“若 `u, v` 不属于给定的任何一组组引导关系，则 `u` 号话题的出现，”
* 有 `n` 个人，`n` 个话题，第 `i` 个话题可以引起第 `c_i` 个人的 `w_i` 分钟激烈发言。
* 话题之间有 `m` 组引导关系 `(u, v)`，即，如果话题 `u` 出现，则话题 `v` 也出现。
* 不存在一个 `c_i = 1` 的话题，能够直接或间接引导另一个 `c_j = 1` 的话题。
* 现在希望选择若干（大于0）个 `c_i = 1` 的话题，使得除了第1个人以外的所有人的激烈发言时间最大值，除以第1个人的激烈发言时间尽可能大。
* 只需求出最大值向下取整的结果。
* I: 猜想，只用考虑群里每个人的答案，然后取max即可
* I: 二分答案，然后对每个人跑一遍maxprofit问题（最大流），会T吗？？？
* I: 知识点：网络流？？？


### K

* E: 题目描述，`ai ⊗oi bi`，这里没有说明 `oi` 是啥
* E: 输入格式，`表示每一个 ⊗i`，应该是表示每一个 `oi` 吧
* 定义一个新的运算 `a[+]b`，表示对 `a` 和 `b` 的每一个二进制位，分别进行给定的二进制操作，得到的数。
* 该二进制操作为**与、或、非**的某一种。
* 容易证明，`a[+]b` 满足交换律、结合律。
* 现给定一张无向图，边有权，求对于所有生成树，`n-1` 个边权的 `[+]` 和的最大值。
* I: 这题我不会
* I: 知识点：这题我不会

### L

* E: 题目描述，喵喵喵？什么是序列的合并？
* E: 题目描述，`R(u) = \xor_{v=1}^n ...`，为啥 `v` 的范围是 `1..n` 而不是 `1..m` 呢？
* W: 样例解释中 `xor` 两侧缺少空格
* 给定一个 `m` 个长度分别是 `n_i` 的序列。
* 定义一个长度为 `n` 的序列（准确说，一个集合）的中位数，为它排序后的第 `floor((n+1)/2)` 小的数。
* 记 `f(u,v)` 为第 `u` 个序列和第 `v` 个序列的并（并集）的中位数。
* 对于所有 `u = 1..m`，求 `R(u) = \xor_{v=1}^m (f(u,v) + u + v)`。
* I: 这题我不会
* I: 知识点：这题我不会

### M

* 给定一个年份（1913-2019），输出母亲节（五月的第二个周日）的日期。
* I: 签到题
* I: 知识点：签到题
