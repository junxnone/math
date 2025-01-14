---
Title | 线性代数 Matrix 正交矩阵
-- | --
Created @ | `2025-01-14T08:36:28Z`
Updated @| `2025-01-14T08:40:39Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/32)

---
# 正交矩阵

- 若一个 $n$ 阶方阵 $A$ 满足 $A^{T}A = AA^{T}=I$ （ $I$ 是 $n$ 阶单位矩阵），则称 $A$ 为正交矩阵。
- 正交矩阵的转置矩阵就是它的逆矩阵，即 $A^{T}=A^{-1}$

$$A=\begin{bmatrix} a_1 & a_2 & ... & a_n \\ \end{bmatrix}$$

$$A^T=\begin{bmatrix} a_1^T \\ a_2^T \\ ... \\ a_n^T \\ \end{bmatrix} $$

$$A^TA = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
\end{bmatrix}$$ 


## 性质
- 正交矩阵的行列式的值为 $\pm1$ 
- 若 $A$ 和 $B$ 是正交矩阵，那么 $AB$ 也是正交矩阵。

## 几何意义
- 在二维空间中，正交矩阵代表旋转和反射变换。
  - 以旋转矩阵为例:

$$\begin{pmatrix}\cos\theta&-\sin\theta\\
\sin\theta&\cos\theta\end{pmatrix}$$

表示将向量逆时针旋转 $\theta$ 角度的变换。

- 在三维空间中，正交矩阵同样可以表示旋转和反射等刚体变换。
  - 例如，绕 $z$ 轴旋转 $\alpha$ 角度的旋转矩阵为:
 
$$R_{z}=\begin{pmatrix}\cos\alpha&-\sin\alpha&0\\
\sin\alpha&\cos\alpha&0\\
0&0&1\end{pmatrix}$$


## 求正交矩阵的方法

### 施密特正交化方法
- 施密特正交化方法：如果已知一组线性无关的向量组 $\left\{\vec{v}_{1},\vec{v}_{2},\cdots,\vec{v}_{n}\right\}$ ，可以通过施密特正交化过程得到一组正交向量组 $\left\{\vec{u}_{1},\vec{u}_{2},\cdots,\vec{u}_{n}\right\}$ ，然后将这些正交向量组单位化，得到标准正交向量组 $\left\{\hat{e}_{1},\hat{e}_{2},\cdots,\hat{e}_{n}\right\}$ 。以这些标准正交向量组为列向量组成的矩阵就是正交矩阵。
