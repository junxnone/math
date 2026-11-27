---
Title | 线性代数 Matrix 克罗内克积
-- | --
Created @ | `2025-01-14T06:47:19Z`
Updated @| `2026-11-27T01:33:07Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/26)

---
# 克罗内克积
- Kronecker product
- 对于矩阵 $A=(a_{ij})$ ，它是一个 $m\times n$ 矩阵，和矩阵 $B=(b_{ij})$ ，它是一个 $p\times q$ 矩阵
- A 与 B 的克罗内克积 $A\otimes B$ 是一个 $mp\times nq$ 矩阵:

$$(A\otimes B)_{(i - 1)p + k,(j - 1)q + l}=a_{ij}b_{kl}$$

其中 $i = 1,\cdots,m$ ， $j = 1,\cdots,n$ ， $k = 1,\cdots,p$ ， $l = 1,\cdots,q$ 。

其中：

- $a_{ij}$：$A$ 的第 $i$ 行第 $j$ 列元素；$b_{kl}$：$B$ 的第 $k$ 行第 $l$ 列元素
- 下标 $(i-1)p+k$ 与 $(j-1)q+l$：把 $A$ 的每个元素 $a_{ij}$ 换成一个 $p\times q$ 的块 $a_{ij}B$，块在大矩阵中的位置由 $(i,j)$ 决定，块内位置由 $(k,l)$ 决定
- 直观：把 $A$ 的每个元素当作系数，各自乘以整个 $B$，再按 $A$ 的排布拼成一个大矩阵

## 示例
假设 

$$A=\begin{pmatrix}a_{11}&a_{12}\ 
a_{21}&a_{22}\end{pmatrix}$$ 
和 
$$B=\begin{pmatrix}b_{11}&b_{12}\ 
b_{21}&b_{22}\end{pmatrix}$$

则它们的克罗内克积 $A\otimes B$ 为：


$$\begin{pmatrix}
a_{11}B & a_{12}B\
a_{21}B & a_{22}B
\end{pmatrix}=\begin{pmatrix}
a_{11}b_{11}&a_{11}b_{12}&a_{12}b_{11}&a_{12}b_{12}\
a_{11}b_{21}&a_{11}b_{22}&a_{12}b_{21}&a_{12}b_{22}\
a_{21}b_{11}&a_{21}b_{12}&a_{22}b_{11}&a_{22}b_{12}\
a_{21}b_{21}&a_{21}b_{22}&a_{22}b_{21}&a_{22}b_{22}
\end{pmatrix}
$$


例如，若 

$$A=\begin{pmatrix}
1 & 2\
3&4\end{pmatrix}$$

$$B=\begin{pmatrix}
5&6\
7&8\end{pmatrix}$$ 

则：

$$
A\otimes B=\begin{pmatrix}
1\times\begin{pmatrix}5&6\
7&8\end{pmatrix}&2\times\begin{pmatrix}5&6\
7&8\end{pmatrix}\
3\times\begin{pmatrix}5&6\
7&8\end{pmatrix}&4\times\begin{pmatrix}5&6\
7&8\end{pmatrix}
\end{pmatrix}=\begin{pmatrix}
5&6&10&12\
7&8&14&16\
15&18&20&24\
21&24&28&32
\end{pmatrix}
$$


## 性质
- **结合律**： $(A\otimes B)\otimes C = A\otimes (B\otimes C)$ 
- **分配律**： $(A + B)\otimes C = A\otimes C + B\otimes C$ 和 $A\otimes (B + C)=A\otimes B + A\otimes C$ （假设矩阵的加法是可定义的）
- **与矩阵乘法的关系**： $(A\otimes B)(C\otimes D)=(AC)\otimes (BD)$ （假设矩阵的乘法是可定义的）
- **不满足交换律**：一般 $A\otimes B\ne B\otimes A$（二者只相差行列置换）
- **转置与逆**：$(A\otimes B)^{T}=A^{T}\otimes B^{T}$；若 $A,B$ 可逆，$(A\otimes B)^{-1}=A^{-1}\otimes B^{-1}$

设 $A$ 为 $m\times m$、$B$ 为 $p\times p$ 方阵，则

$$
\det(A\otimes B)=\det(A)^{p}\det(B)^{m},\qquad \mathrm{rank}(A\otimes B)=\mathrm{rank}(A)\,\mathrm{rank}(B),\qquad \mathrm{tr}(A\otimes B)=\mathrm{tr}(A)\,\mathrm{tr}(B)
$$

其中：$A$ 的特征值为 $\lambda_i$、$B$ 的特征值为 $\mu_j$ 时，$A\otimes B$ 的特征值恰为所有乘积 $\lambda_i\mu_j$，上面三个式子都可以由此得到。

## 与向量化的联系

$$
\mathrm{vec}(AXB)=(B^{T}\otimes A)\,\mathrm{vec}(X)
$$

其中：

- $\mathrm{vec}(X)$：把矩阵 $X$ 按列依次拼成的长向量
- 这个恒等式把「矩阵方程」$AXB=C$（如 Sylvester 方程）转化成标准的线性方程组 $(B^T\otimes A)x=c$，是克罗内克积最常见的用途

## 与其他乘积对比

| 运算 | 符号 | 结果形状 | 含义 |
| --- | --- | --- | --- |
| 矩阵乘积 | $AB$ | $m\times p$ | 线性变换复合，见 [矩阵乘积](https://github.com/junxnone/math/issues/27) |
| 哈达玛积 | $A\circ B$ | 同形 | 逐元素相乘，见 [哈达玛乘积](https://github.com/junxnone/math/issues/28) |
| 克罗内克积 | $A\otimes B$ | $mp\times nq$ | 分块放大，$A$ 的每个元素乘以整个 $B$ |

表中：对比结论：克罗内克积会让矩阵的维数相乘，规模增长很快，实际计算通常利用其结构（不显式构造大矩阵）。

## 应用
- **线性系统和线性方程**：在求解大型线性方程组时，如果方程组可以表示为克罗内克积的形式，可以利用克罗内克积的性质来简化求解过程。
- **图像处理**：在图像处理中，克罗内克积可用于图像的缩放、分块等操作。例如，将一个小的图像矩阵与一个适当的矩阵进行克罗内克积，可以实现图像的放大。
- **信号处理**：在信号处理中，克罗内克积可以用于多通道信号的表示和处理，将不同通道的信号表示为克罗内克积的形式，方便进行信号的变换和分析。
- **机器学习**：二维可分离滤波、K-FAC 近似二阶优化（用克罗内克积近似 Fisher 矩阵）、张量分解（见 [张量基础](https://github.com/junxnone/math/issues/47)）。

克罗内克积在不同的数学和工程领域都有广泛的应用，其特殊的矩阵结构和运算性质为解决复杂的矩阵相关问题提供了一种有效的工具。

