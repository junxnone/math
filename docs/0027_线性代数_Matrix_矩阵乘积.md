---
Title | 线性代数 Matrix 矩阵乘积
-- | --
Created @ | `2025-01-14T07:02:28Z`
Updated @| `2025-01-14T07:02:28Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/27)

---
# 矩阵乘积
- **Matrix Product** 
- $C = AB$ 
  - 矩阵 A 的列数必须和矩 阵 B 的行数相等。
  - $C_{ij}=\sum_{k}A_{ik}B_{k j}$

## 乘积性质

- **交换律:** $A \circ B = B \circ A$ 的情况并非总是满足
- **结合律:** $A \circ (B \circ C) = (A \circ B) \circ C$
- **分配律:** $A \circ (B + C) = A \circ B + A \circ C$

## 例子

$$A=\begin{pmatrix}
a_{11} & a_{12} & \cdots & a_{1n}\\
a_{21} & a_{22} & \cdots & a_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{pmatrix}$$


$$B=\begin{pmatrix}
b_{11} & b_{12} & \cdots & b_{1k}\\
b_{21} & b_{22} & \cdots & b_{2k}\\
\vdots & \vdots & \ddots & \vdots\\
b_{n1} & b_{n2} & \cdots & b_{nk}
\end{pmatrix}$$

$$C=\begin{pmatrix}
c_{11} & c_{12} & \cdots & c_{1k}\\
c_{21} & c_{22} & \cdots & c_{2k}\\
\vdots & \vdots & \ddots & \vdots\\
c_{m1} & c_{m2} & \cdots & c_{mk}
\end{pmatrix}$$

$c_{ik}=\sum_{j = 1}^{n}a_{ij}b_{jk}$

$c_{11}=a_{11}b_{11}+a_{12}b_{21}+\cdots + a_{1n}b_{n1}$

$c_{12}=a_{11}b_{12}+a_{12}b_{22}+\cdots + a_{1n}b_{n2}$

$\cdots$

$c_{1k}=a_{11}b_{1k}+a_{12}b_{2k}+\cdots + a_{1n}b_{nk}$


$c_{21}=a_{21}b_{11}+a_{22}b_{21}+\cdots + a_{2n}b_{n1}$

$c_{22}=a_{21}b_{12}+a_{22}b_{22}+\cdots + a_{2n}b_{n2}$

$\cdots$

$c_{2k}=a_{21}b_{1k}+a_{22}b_{2k}+\cdots + a_{2n}b_{nk}$


$\cdots$


$c_{m1}=a_{m1}b_{11}+a_{m2}b_{21}+\cdots + a_{mn}b_{n1}$

$c_{m2}=a_{m1}b_{12}+a_{m2}b_{22}+\cdots + a_{mn}b_{n2}$

$\cdots$

$c_{mk}=a_{m1}b_{1k}+a_{m2}b_{2k}+\cdots + a_{mn}b_{nk}$



