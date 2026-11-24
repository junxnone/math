---
Title | 线性代数 Matrix 初等变换
-- | --
Created @ | `2026-11-24T10:06:44Z`
Updated @| `2026-11-24T10:06:44Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/38)

---
# 初等变换

初等变换是解线性方程组、求秩和求逆矩阵的基本工具：它们改变矩阵的外形，但不改变（或可控地改变）矩阵的关键性质。

## 三种初等行变换

| 类型 | 操作 | 记法 |
| -- | -- | -- |
| 交换 | 交换两行 | $R_i\leftrightarrow R_j$ |
| 倍乘 | 某一行乘以非零常数 $k$ | $kR_i$ |
| 倍加 | 某一行加上另一行的 $k$ 倍 | $R_i+kR_j$ |

表中三列分别是变换类型、具体操作和常用记法，$R_i$ 表示第 $i$ 行。把“行”换成“列”即得初等列变换，记法为 $C_i$。每种变换都是可逆的，逆变换仍是同类变换（交换的逆是自身，$kR_i$ 的逆是 $\frac1kR_i$，$R_i+kR_j$ 的逆是 $R_i-kR_j$）。

## 初等矩阵

每一次初等行变换等价于左乘一个初等矩阵（对单位矩阵 $I$ 做同样变换得到），列变换则对应右乘：

$$
A\ \xrightarrow{\text{行变换}}\ EA,\qquad A\ \xrightarrow{\text{列变换}}\ AE
$$

其中：

- $E$：初等矩阵，由单位矩阵经一次初等变换得到，一定可逆
- 例：交换 2×2 矩阵两行对应 $E=\begin{bmatrix}0&1\\1&0\end{bmatrix}$；第 2 行加上第 1 行的 $k$ 倍对应 $E=\begin{bmatrix}1&0\\k&1\end{bmatrix}$
- 一系列变换对应 $E_k\cdots E_2E_1A$；由于初等矩阵可逆，变换前后矩阵“等价”，保持秩不变

## 行阶梯形与行最简形

- 行阶梯形（REF）：全零行在底部；每行第一个非零元（主元）位于上一行主元的右侧，主元下方全为 0。
- 行最简形（RREF）：在行阶梯形基础上，每个主元为 1，且主元所在列的其他元素均为 0。

任何矩阵都可以只用行变换化为行阶梯形（高斯消元），进一步化为唯一的行最简形（高斯-若尔当消元）。例（化为行阶梯形）：

$$
\begin{bmatrix}1&2&3\\2&4&7\\1&2&4\end{bmatrix}
\xrightarrow[R_3-R_1]{R_2-2R_1}
\begin{bmatrix}1&2&3\\0&0&1\\0&0&1\end{bmatrix}
\xrightarrow{R_3-R_2}
\begin{bmatrix}1&2&3\\0&0&1\\0&0&0\end{bmatrix}
$$

其中：

- 主元分别是第 1 行的 1（第 1 列）和第 2 行的 1（第 3 列），共 2 个
- 第 3 行化为全零，说明原矩阵的第 3 行是前两行的线性组合（线性相关，见 [线性相关无关](https://github.com/junxnone/math/issues/24)）

## 应用

### 求秩

行阶梯形中非零行（主元）的个数就是矩阵的秩。上例中 $\operatorname{rank}(A)=2$（见 [秩](https://github.com/junxnone/math/issues/29)）。

### 求逆矩阵

对增广矩阵 $[A\mid I]$ 做行变换，把左半部分化为 $I$，右半部分即为 $A^{-1}$：

$$
[A\mid I]\ \xrightarrow{\text{行变换}}\ [I\mid A^{-1}]
$$

其中：

- $A$：待求逆的 $n$ 阶方阵；$I$：同阶单位矩阵
- 原理：若 $E_k\cdots E_1A=I$，则 $E_k\cdots E_1=A^{-1}$，对 $I$ 做相同变换就得到 $A^{-1}$
- 左半部分无法化为 $I$（出现全零行）说明 $A$ 不可逆

例：$A=\begin{bmatrix}1&2\\3&4\end{bmatrix}$。

$$
\left[\begin{array}{cc|cc}1&2&1&0\\3&4&0&1\end{array}\right]
\xrightarrow{R_2-3R_1}
\left[\begin{array}{cc|cc}1&2&1&0\\0&-2&-3&1\end{array}\right]
\xrightarrow{-\frac12R_2}
\left[\begin{array}{cc|cc}1&2&1&0\\0&1&\frac32&-\frac12\end{array}\right]
\xrightarrow{R_1-2R_2}
\left[\begin{array}{cc|cc}1&0&-2&1\\0&1&\frac32&-\frac12\end{array}\right]
$$

得 $A^{-1}=\begin{bmatrix}-2&1\\\frac32&-\frac12\end{bmatrix}$。验证：第 1 行乘 $A$ 的第 1 列 $-2\cdot1+1\cdot3=1$，第 1 行乘第 2 列 $-2\cdot2+1\cdot4=0$。

### 解线性方程组

对增广矩阵 $[A\mid\mathbf{b}]$ 做行变换不改变方程组的解，化为行阶梯形后回代即可（见 [线性方程组](https://github.com/junxnone/math/issues/35)）。

### 对行列式的影响

| 行变换 | 行列式变化 |
| -- | -- |
| $R_i\leftrightarrow R_j$ | 变号：$\det\to-\det$ |
| $kR_i$ | 乘以 $k$：$\det\to k\det$ |
| $R_i+kR_j$ | 不变 |

表中左列是行变换，右列是对行列式的影响，因此用倍加变换化为上三角矩阵后，行列式等于对角线乘积（乘以交换次数对应的符号），这就是行列式的“等价转换法”（见 [Determinant](https://github.com/junxnone/math/issues/3)）。

## Reference

- [Elementary matrix - Wikipedia](https://en.wikipedia.org/wiki/Elementary_matrix)
- [Row echelon form - Wikipedia](https://en.wikipedia.org/wiki/Row_echelon_form)

