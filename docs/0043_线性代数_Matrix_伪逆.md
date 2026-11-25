---
Title | 线性代数 Matrix 伪逆
-- | --
Created @ | `2026-11-24T14:42:23Z`
Updated @| `2026-11-25T09:33:36Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/43)

---
# 伪逆

伪逆（Moore-Penrose 广义逆）把“逆”推广到任意矩阵，包括非方阵和奇异矩阵。它给出线性方程组的最小二乘解中范数最小的那一个。

## 定义（Penrose 条件）

$A\in\mathbb{R}^{m\times n}$ 的伪逆 $A^+\in\mathbb{R}^{n\times m}$ 是唯一满足下面四个条件的矩阵：

$$
AA^+A=A,\qquad A^+AA^+=A^+,\qquad (AA^+)^\top=AA^+,\qquad (A^+A)^\top=A^+A
$$

其中：

- 前两条说明 $A^+$ 在 $A$ 的“有效部分”上起逆的作用
- 后两条说明 $AA^+$ 与 $A^+A$ 是对称矩阵，即正交投影矩阵（见 [投影](/0042_线性代数_投影)）：$AA^+$ 投影到 $\operatorname{Col}(A)$，$A^+A$ 投影到 $\operatorname{Row}(A)$
- $A$ 可逆时 $A^+=A^{-1}$

## 由 SVD 计算

设 $A=U\Sigma V^\top$（见 [SVD](/0012_线性代数_SVD)），则：

$$
A^+=V\Sigma^+U^\top,\qquad \Sigma^+_{ii}=\begin{cases}1/\sigma_i&\sigma_i>0\\0&\sigma_i=0\end{cases}
$$

其中：

- $U,V$：正交矩阵；$\sigma_i$：奇异值
- $\Sigma^+\in\mathbb{R}^{n\times m}$：把 $\Sigma$ 转置，并对非零奇异值取倒数、零保持为零
- 数值计算时，小于阈值（如 $\varepsilon\cdot\sigma_{\max}\cdot\max(m,n)$）的奇异值视为 0，否则噪声会被放大；阈值同时决定了数值秩

例：$\operatorname{diag}(2,0)^+=\operatorname{diag}(\tfrac12,0)$：能求逆的方向取倒数，被压扁的方向不恢复。

## 特殊情形的公式

| 情形 | 条件 | 伪逆 |
| -- | -- | -- |
| 可逆方阵 | $\operatorname{rank}(A)=m=n$ | $A^{-1}$ |
| 列满秩（高瘦） | $\operatorname{rank}(A)=n<m$ | $(A^\top A)^{-1}A^\top$ |
| 行满秩（矮胖） | $\operatorname{rank}(A)=m<n$ | $A^\top(AA^\top)^{-1}$ |

表中列依次为情形、秩条件和伪逆公式。例：$A=\begin{bmatrix}1\\1\end{bmatrix}$ 列满秩，$A^+=\tfrac12\begin{bmatrix}1&1\end{bmatrix}$，$A^+A=1$。列满秩的公式即最小二乘的正规方程解（见 [线性方程组](/0035_线性代数_线性方程组)）。

## 解的意义

$$
\hat{\mathbf{x}}=A^+\mathbf{b}
$$

其中：

- $\hat{\mathbf{x}}$：在所有使 $\|A\mathbf{x}-\mathbf{b}\|_2$ 最小的 $\mathbf{x}$ 中，范数 $\|\mathbf{x}\|_2$ 最小的那一个
- $A\mathbf{x}=\mathbf{b}$ 有唯一解：$\hat{\mathbf{x}}$ 就是该解
- 有无穷多解：$\hat{\mathbf{x}}$ 是其中范数最小者，位于行空间内
- 无解：$\hat{\mathbf{x}}$ 是最小二乘解，$A\hat{\mathbf{x}}$ 是 $\mathbf{b}$ 在列空间上的投影

## 应用

- 欠定/病态方程组的稳健求解；机器人逆运动学中用雅可比伪逆求关节速度（见 [雅可比矩阵](/0044_线性代数_Matrix_雅可比矩阵)）
- 线性回归的闭式解；带正则化的岭回归可看作对小奇异值做平滑：$\sigma_i/(\sigma_i^2+\lambda)$ 替代 $1/\sigma_i$
- 低秩近似：保留 $k$ 个最大奇异值得到最佳秩 $k$ 逼近

## Reference

- [Moore-Penrose inverse - Wikipedia](https://en.wikipedia.org/wiki/Moore%E2%80%93Penrose_inverse)


