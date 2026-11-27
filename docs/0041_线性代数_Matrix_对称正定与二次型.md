---
Title | 线性代数 Matrix 对称正定与二次型
-- | --
Created @ | `2026-11-24T14:42:18Z`
Updated @| `2026-11-27T01:42:44Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/41)

---
# 对称正定与二次型

二次型是关于向量各分量的二次齐次多项式，可以用对称矩阵紧凑表示。矩阵是否“正定”决定了二次型的形状：碗状（有最小值）、鞍形或倒碗，这是优化、协方差、能量函数分析的基础。

## 二次型

$$
q(\mathbf{x})=\mathbf{x}^\top A\mathbf{x}=\sum_{i,j}a_{ij}x_ix_j
$$

其中：

- $\mathbf{x}\in\mathbb{R}^n$：变量向量
- $A\in\mathbb{R}^{n\times n}$：系数矩阵；不失一般性取对称，因为 $\mathbf{x}^\top A\mathbf{x}=\mathbf{x}^\top\tfrac{A+A^\top}{2}\mathbf{x}$
- $q(\mathbf{x})$：标量；例：$A=\begin{bmatrix}2&-1\\-1&2\end{bmatrix}$ 时 $q=2x_1^2-2x_1x_2+2x_2^2$

## 定性分类

| 类型 | 条件 | 特征值 |
| -- | -- | -- |
| 正定 | $\mathbf{x}^\top A\mathbf{x}>0\ (\mathbf{x}\ne\mathbf{0})$ | 全部 $>0$ |
| 半正定 | $\mathbf{x}^\top A\mathbf{x}\ge0$ | 全部 $\ge0$ |
| 负定 | $\mathbf{x}^\top A\mathbf{x}<0\ (\mathbf{x}\ne\mathbf{0})$ | 全部 $<0$ |
| 不定 | 取值有正有负 | 有正有负 |

表中列依次为类型、定义条件和对应的特征值符号。对称矩阵的特征值都是实数（见 [特征值与特征向量](/0036_线性代数_特征值与特征向量)），由此可以判定正定性。

## 正定的判定

- 特征值法：所有特征值 $\lambda_i>0$。
- 顺序主子式（Sylvester 准则）：各阶顺序主子式 $\Delta_k=\det A_{1:k,1:k}>0\ (k=1,\dots,n)$。
- Cholesky 法：能做 Cholesky 分解 $A=LL^\top$ 且对角线为正（见 [矩阵分解](/0040_线性代数_Matrix_矩阵分解)）。
- 必要条件：对角线元素全为正；$\det A>0$。

例：$A=\begin{bmatrix}2&-1\\-1&2\end{bmatrix}$，特征值 $1,3>0$；顺序主子式 $2>0$，$\det A=3>0$，所以正定。

## 重要结论：$A^\top A$ 半正定

$$
\mathbf{x}^\top(A^\top A)\mathbf{x}=\|A\mathbf{x}\|_2^2\ge0
$$

其中：

- $A\in\mathbb{R}^{m\times n}$：任意矩阵；$\|A\mathbf{x}\|_2$：向量 $A\mathbf{x}$ 的 $L_2$ 范数
- 因此 $A^\top A$ 总是半正定；当 $A$ 列满秩时严格正定（$A\mathbf{x}=\mathbf{0}$ 只有零解）
- 这就是最小二乘正规方程中 $A^\top A$ 可逆、SVD 中奇异值 $\sigma_i=\sqrt{\lambda_i}$ 有意义的原因

## 几何意义

对称正定矩阵 $A=Q\Lambda Q^\top$ 时，等值面 $\mathbf{x}^\top A\mathbf{x}=1$ 是椭圆（三维为椭球）：

- 主轴方向是特征向量 $\mathbf{q}_i$（$Q$ 的列）
- 沿 $\mathbf{q}_i$ 的半轴长为 $1/\sqrt{\lambda_i}$：特征值越大，该方向越“陡”、半轴越短
- 作换元 $\mathbf{y}=Q^\top\mathbf{x}$ 可消去交叉项：$q=\sum_i\lambda_iy_i^2$（标准形）

## 应用

- 协方差矩阵：$\mathbf{w}^\top\Sigma\mathbf{w}=\operatorname{Var}(\mathbf{w}^\top\mathbf{X})\ge0$，所以协方差矩阵半正定；高斯分布要求 $\Sigma$ 正定（见 [Gaussian Distribution](/0005_概率论_常见分布_高斯分布进阶)）
- 优化：Hessian 矩阵 $H$ 在驻点处正定 $\Rightarrow$ 严格局部极小；负定 $\Rightarrow$ 极大；不定 $\Rightarrow$ 鞍点。凸二次函数 $\tfrac12\mathbf{x}^\top A\mathbf{x}-\mathbf{b}^\top\mathbf{x}$ 的最小点满足 $A\mathbf{x}=\mathbf{b}$
- 距离度量：马氏距离 $d^2=(\mathbf{x}-\boldsymbol\mu)^\top\Sigma^{-1}(\mathbf{x}-\boldsymbol\mu)$ 即以 $\Sigma^{-1}$ 为核的二次型

## Reference

- [Definite matrix - Wikipedia](https://en.wikipedia.org/wiki/Definite_matrix)
- Gilbert Strang, *Introduction to Linear Algebra*, Chapter 6



