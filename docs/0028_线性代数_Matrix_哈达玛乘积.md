---
Title | 线性代数 Matrix 哈达玛乘积
-- | --
Created @ | `2025-01-14T07:04:52Z`
Updated @| `2026-11-27T01:33:05Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/28)

---
# 哈达玛乘积

 - **Hadamard Product**/**Element-Wise Product**
 - 两个**同形**矩阵对应位置元素相乘，得到同形矩阵：$(A\circ B)_{ij}=A_{ij}B_{ij}$

其中：$A,B$ 为同为 $m\times n$ 的矩阵；$\circ$（或 $\odot$）为哈达玛乘积符号；结果 $C=A\circ B$ 仍是 $m\times n$ 矩阵。

## 性质
- **交换律:** $A \circ B = B \circ A$ 
- **结合律:** $A \circ (B \circ C) = (A \circ B) \circ C$
- **分配律:** $A \circ (B + C) = A \circ B + A \circ C$
- **单位元：** 全 1 矩阵 $J$：$A\circ J=A$
- **与转置：** $(A\circ B)^{T}=A^{T}\circ B^{T}$

> $\circ$ 与 $\odot$ 都可以表示哈达玛积（与「点积」无关，点积指向量内积）

## 例子

$$\left[ \begin{array}{ccc}    
 a_{11} & a_{12} & a_{13}\ 
 a_{21} & a_{22} & a_{23}\
 a_{31} & a_{32} & a_{33} 
\end{array} \right] \circ 
\left[ \begin{array}{ccc} 
    b_{11} & b_{12} & b_{13}\
    b_{21} & b_{22} & b_{23}\
    b_{31} & b_{32} & b_{33} \end{array} \right] = 
\left[ \begin{array}{ccc}
     a_{11}\times b_{11} & a_{12}\times b_{12} & a_{13}\times b_{13}\
     a_{21}\times b_{21} & a_{22}\times b_{22} & a_{23}\times b_{23}\
     a_{31}\times b_{31} & a_{32}\times b_{32} & a_{33}\times b_{33}
 \end{array} \right]$$

数值例：

$$
\begin{bmatrix}1&2\3&4\end{bmatrix}\circ\begin{bmatrix}5&6\7&8\end{bmatrix}=\begin{bmatrix}5&12\21&32\end{bmatrix}
$$

## 与矩阵乘积的关系

| 对比项 | 矩阵乘积 $AB$ | 哈达玛积 $A\circ B$ |
| --- | --- | --- |
| 形状要求 | $A$ 的列数 = $B$ 的行数 | 两者同形 |
| 计算 | 行与列的点乘求和 | 对应元素相乘 |
| 交换律 | 一般不成立 | 成立 |
| 几何意义 | 线性变换的复合 | 逐元素缩放 |
| 计算量 | $O(mnp)$ | $O(mn)$ |

表中：对比结论：哈达玛积是「元素级」运算，不涉及行列之间的求和，计算量小得多。

几个联系：

$$
\mathrm{tr}(A^{T}B)=\sum_{i,j}(A\circ B)_{ij},\qquad \mathrm{diag}(a)\,x=a\circ x
$$

其中：

- 第一式：$A^TB$ 的迹等于哈达玛积所有元素之和，即把两个矩阵看作向量后的内积（Frobenius 内积）
- 第二式：$\mathrm{diag}(a)$ 为以向量 $a$ 为对角线的对角矩阵；用对角矩阵左乘向量，等价于与 $a$ 做哈达玛积

**Schur 乘积定理**：两个半正定矩阵的哈达玛积仍是半正定矩阵，见 [对称正定与二次型](https://github.com/junxnone/math/issues/41)。

## 在机器学习中的作用

- 掩码：用 0/1 矩阵逐元素相乘，屏蔽某些位置（注意力掩码、Dropout）
- 门控机制：LSTM / GRU 中的门 $g\circ h$，逐元素决定通过多少信息
- 梯度：激活函数的反向传播 $\delta=(W^{T}\delta')\circ f'(z)$，需要逐元素乘激活函数的导数
- 特征缩放与权重调制

## 相关文章

- [矩阵乘积](https://github.com/junxnone/math/issues/27)、[克罗内克积](https://github.com/junxnone/math/issues/26)、[矩阵](https://github.com/junxnone/math/issues/4)

