---
Title | 线性代数 Matrix
-- | --
Created @ | `2022-04-19T11:36:53Z`
Updated @| `2025-01-02T00:47:56Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/4)

---
# 矩阵


- 行列变换
- 加减
- 乘法
- 哈达玛乘积 - `Hadamard product`
- 转置
- 逆
- 秩
- 迹
- 雅可比行列式 - Jacobi



## 矩阵转置
- **矩阵转置**: 矩阵 A 元素行列交换得到的转置矩阵 $A^{T}$ 

$$A = \begin{vmatrix}
a_{11} & a_{12} & ... & a_{1n} \\
a_{21} & a_{22} & ... & a_{2n} \\
... & ... & ... & ... \\
a_{m1} & a_{m2} & ... & a_{mn} \\
\end{vmatrix}$$

$$A^T = \begin{vmatrix}
a_{11} & a_{21} & ... & a_{m1} \\
a_{12} & a_{22} & ... & a_{m2} \\
... & ... & ... & ... \\
a_{1n} & a_{2n} & ... & a_{mn} \\
\end{vmatrix}$$

### 转置性质

- $(A^T)^T=A$
- $(A+B)^T=A^T+B^T$
- $(\lambda A)^T=\lambda A^T$
- $(AB)^T=B^TA^T$

## 矩阵的逆
- **矩阵逆**: $AA^{-1}=A^{-1}A=E$
  - 对于一个 n 阶方阵 A, 如果存在另一个 n 阶方阵 B 满足 $AB=BA=E$, E 为单位矩阵 
  - 即 $B=A^{-1}$
  - A B 互为逆矩阵

## 正交矩阵
- **正交矩阵**: $A^TA=E$

$$A=\begin{bmatrix} a_1 & a_2 & ... & a_n \\ \end{bmatrix}$$

$$A^T=\begin{bmatrix} a_1^T \\ a_2^T \\ ... \\ a_n^T \\ \end{bmatrix} $$

$$A^TA = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
\end{bmatrix}$$ 

## 运算定义 

#### Hadamard Product
- $A \circ B = B \circ A$
- $A \circ (B \circ C) = (A \circ B) \circ C$
- $A \circ (B + C) = A \circ B + A \circ C$

$$\left[ \begin{array}{ccc}    
 a_{11} & a_{12} & a_{13}\\ 
 a_{21} & a_{22} & a_{23}\\
 a_{31} & a_{32} & a_{33} 
\end{array} \right] \circ 
\left[ \begin{array}{ccc} 
    b_{11} & b_{12} & b_{13}\\
    b_{21} & b_{22} & b_{23}\\
    b_{31} & b_{32} & b_{33} \end{array} \right] = 
\left[ \begin{array}{ccc}
     a_{11}\times b_{11} & a_{12}\times b_{12} & a_{13}\times b_{13}\\
     a_{21}\times b_{21} & a_{22}\times b_{22} & a_{23}\times b_{23}\\
     a_{31}\times b_{31} & a_{32}\times b_{32} & a_{33}\times b_{33}
 \end{array} \right]$$


## Reference
- [矩阵的运算及其运算规则](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/ch0605.html)

