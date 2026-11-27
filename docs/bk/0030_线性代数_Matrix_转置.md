-----

| Title     | 线性代数 Matrix 转置                                     |
| --------- | -------------------------------------------------- |
| Created @ | `2025-01-14T08:11:36Z`                             |
| Updated @ | `2026-11-27T01:33:00Z`                             |
| Labels    | \`\`                                               |
| Edit @    | [here](https://github.com/junxnone/math/issues/30) |

-----

# 矩阵转置

  - **矩阵转置**: 矩阵 A 元素行列交换得到的转置矩阵 $A^{T}$

$$A = \\begin{bmatrix} a\_{11} & a\_{12} & ... & a\_{1n}   
a\_{21} & a\_{22} & ... & a\_{2n}   
... & ... & ... & ...   
a\_{m1} & a\_{m2} & ... & a\_{mn}   
\\end{bmatrix}$$

$$A^T = \\begin{bmatrix} a\_{11} & a\_{21} & ... & a\_{m1}   
a\_{12} & a\_{22} & ... & a\_{m2}   
... & ... & ... & ...   
a\_{1n} & a\_{2n} & ... & a\_{mn}   
\\end{bmatrix}$$

其中：

  - $A$：$m\\times n$ 矩阵（$m$ 行 $n$ 列）；$A^{T}$（也写作 $A^\\top$）：$n\\times m$
    矩阵
  - 元素关系：$(A^{T})*{ij}=A*{ji}$，即第 $i$ 行第 $j$ 列的元素变成第 $j$ 行第 $i$ 列
  - 行变列、列变行；对角线元素不变

例：

$$ A=\\begin{bmatrix}1&2&3\\4&5&6\\end{bmatrix}\\ \\Longrightarrow\\
A^{T}=\\begin{bmatrix}1&4\\2&5\\3&6\\end{bmatrix} $$

## 转置性质

  - $(A^T)^T=A$
  - $(A+B)^T=A^T+B^T$
  - $(\\lambda A)^T=\\lambda A^T$
  - $(AB)^T=B^TA^T$（顺序反过来）
  - 若 $A$
    可逆，$(A^{-1})^T=(A^T)^{-1}$；$\\det(A^T)=\\det(A)$；$\\mathrm{tr}(A^T)=\\mathrm{tr}(A)$；$\\mathrm{rank}(A^T)=\\mathrm{rank}(A)$

## 对称与反对称

$$ A=A^{T}\\ (\\text{对称}),\\qquad A=-A^{T}\\ (\\text{反对称}),\\qquad
A=\\underbrace{\\tfrac12(A+A^{T})}*{\\text{对称部分}}+\\underbrace{\\tfrac12(A-A^{T})}*{\\text{反对称部分}}
$$

其中：

  - 对称矩阵：沿主对角线镜像相等；反对称矩阵：主对角线元素全为 0，且 $a\_{ij}=-a\_{ji}$
  - 任意方阵都可以唯一地分解为一个对称矩阵与一个反对称矩阵之和
  - 对称矩阵的特征值都是实数，且可以正交对角化，见
    [特征值与特征向量](https://github.com/junxnone/math/issues/36)、[对称正定与二次型](https://github.com/junxnone/math/issues/41)

## 向量的内积与外积

设 $x,y\\in\\mathbb{R}^n$ 为列向量：

$$ x^{T}y=\\sum\_{i=1}^{n}x\_iy\_i\\ (\\text{标量}),\\qquad
xy^{T}=\\begin{bmatrix}x\_iy\_j\\end{bmatrix}\_{n\\times n}\\
(\\text{矩阵，秩为 }1) $$

其中：$x^Ty$ 是内积（点乘），$xy^T$ 是外积；转置让「列向量」变成「行向量」，从而把向量运算写成矩阵乘法。

## 转置的常见出场

| 场景    | 表达式                                | 说明                                                       |
| ----- | ---------------------------------- | -------------------------------------------------------- |
| 最小二乘  | $A^{T}A,\\beta=A^{T}y$             | 正规方程，$A^TA$ 总是对称半正定                                      |
| 协方差矩阵 | $\\Sigma=\\tfrac1n X^{T}X$（数据已中心化） | 对称半正定                                                    |
| 二次型   | $x^{T}Ax$                          | 见 [对称正定与二次型](https://github.com/junxnone/math/issues/41) |
| 正交矩阵  | $Q^{T}Q=I$                         | 见 [正交矩阵](https://github.com/junxnone/math/issues/32)     |

表中：对比结论：转置是把「线性代数的内积结构」写进矩阵运算的工具，$A^TA$ 和 $AA^T$ 总是对称的。

## 常见误区

  - $(AB)^T=B^TA^T$：不能写成 $A^TB^T$（维度可能都对不上）
  - 转置不改变行列式和秩，但会改变矩阵的「形状」；对非方阵，$A^T$ 的维度与 $A$ 不同
  - 复数矩阵常用**共轭转置** $A^{H}=\\overline{A}^{T}$，对应实数情形的转置

## 相关文章

  - [矩阵](https://github.com/junxnone/math/issues/4)、[矩阵乘积](https://github.com/junxnone/math/issues/27)、[正交矩阵](https://github.com/junxnone/math/issues/32)、[矩阵的迹](https://github.com/junxnone/math/issues/37)
