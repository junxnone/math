---
Title | 线性代数 Matrix
-- | --
Created @ | `2022-04-19T11:36:53Z`
Updated @| `2025-01-14T07:54:00Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/4)

---
# 矩阵


- 行列变换
- 乘法
- 转置
- 逆
- 秩
- 迹
- 雅可比行列式 - Jacobi

## 矩阵的秩
- 对于一个 $m\times n$ 矩阵 $A$ ，其秩 $rank(A)$ 定义为矩阵 $A$ 中线性无关的行向量（或列向量）的最大数目。

对于一个简单的 $2\times2$ 矩阵:

$$A=\begin{pmatrix}1&0\\
0&1\end{pmatrix}$$

它的行向量 

$$\vec{r}_{1}=(1,0)$$

$$\vec{r}_{2}=(0,1)$$

 是线性无关的

列向量 

$$\vec{c}_{1}=\begin{pmatrix}1\\
0\end{pmatrix}$$

$$\vec{c}_{2}=\begin{pmatrix}0\\
1\end{pmatrix}$$

也是线性无关的。所以这个矩阵的秩为 $2$ 。

### 秩的性质
 -  $rank(A)=rank(A^{T})$ ，即矩阵 $A$ 的秩等于其转置矩阵 $A^{T}$ 的秩。
 - 如果 $A$ 是 $m\times n$ 矩阵， $B$ 是 $n\times p$ 矩阵，则 $rank(AB)\leq\min\{rank(A),rank(B)\}$ 。
 - 对于 $n$ 阶方阵 $A$ ， $A$ 可逆的充分必要条件是 $rank(A)=n$ 。


### 计算方法
#### 初等变换法
- 可以通过对矩阵进行初等行变换（包括交换两行、某一行乘以一个非零常数、某一行加上另一行的倍数）将矩阵化为阶梯形矩阵。阶梯形矩阵中非零行的行数就是原矩阵的秩。

#### 利用行列式计算
- 对于一个 $n$ 阶方阵 $A$ ，如果 $\vert A\vert\neq0$ ，则 $rank(A) = n$ ；如果 $\vert A\vert = 0$ ，则 $rank(A)<n$ 。

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
- 乘积
  - 矩阵乘积
  - 哈达玛乘积 Hadamard Product
  - 克罗内克积 Kronecker Product



## Reference
- [矩阵的运算及其运算规则](http://www2.edu-edu.com.cn/lesson_crs78/self/j_0022/soft/ch0605.html)

