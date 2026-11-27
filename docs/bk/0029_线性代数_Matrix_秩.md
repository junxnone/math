-----

| Title     | 线性代数 Matrix 秩                                      |
| --------- | -------------------------------------------------- |
| Created @ | `2025-01-14T08:09:57Z`                             |
| Updated @ | `2026-11-27T01:33:09Z`                             |
| Labels    | \`\`                                               |
| Edit @    | [here](https://github.com/junxnone/math/issues/29) |

-----

# 矩阵的秩

  - 对于一个 $m\\times n$ 矩阵 $A$ ，其秩 $rank(A)$ 定义为矩阵 $A$
    中线性无关的行向量（或列向量）的最大数目。

对于一个简单的 $2\\times2$ 矩阵:

$$A=\\begin{pmatrix}1&0\\ 0&1\\end{pmatrix}$$

它的行向量

$$\\vec{r}\_{1}=(1,0)$$

$$\\vec{r}\_{2}=(0,1)$$

是线性无关的

列向量

$$\\vec{c}\_{1}=\\begin{pmatrix}1\\ 0\\end{pmatrix}$$

$$\\vec{c}\_{2}=\\begin{pmatrix}0\\ 1\\end{pmatrix}$$

也是线性无关的。所以这个矩阵的秩为 $2$ 。

## 秩的性质

  - $rank(A)=rank(A^{T})$ ，即矩阵 $A$ 的秩等于其转置矩阵 $A^{T}$ 的秩。
  - 如果 $A$ 是 $m\\times n$ 矩阵， $B$ 是 $n\\times p$ 矩阵，则
    $rank(AB)\\leq\\min{rank(A),rank(B)}$ 。
  - 对于 $n$ 阶方阵 $A$ ， $A$ 可逆的充分必要条件是 $rank(A)=n$ 。

## 计算方法

### 初等变换法

  - 可以通过对矩阵进行初等行变换（包括交换两行、某一行乘以一个非零常数、某一行加上另一行的倍数）将矩阵化为阶梯形矩阵。阶梯形矩阵中非零行的行数就是原矩阵的秩。

### 利用行列式计算

  - 对于一个 $n$ 阶方阵 $A$ ，如果 $\\vert A\\vert\\neq0$ ，则 $rank(A) = n$ ；如果
    $\\vert A\\vert = 0$ ，则 $rank(A)\<n$ 。

## 秩与子空间

$$ \\operatorname{rank}(A)+\\dim\\operatorname{Null}(A)=n $$

其中：

  - $A\\in\\mathbb{R}^{m\\times n}$：矩阵，$n$ 为列数
  - $\\operatorname{rank}(A)$：列空间（也是行空间）的维数
  - $\\operatorname{Null}(A)={\\mathbf{x}\\mid
    A\\mathbf{x}=\\mathbf{0}}$：零空间；该式称为秩-零化度定理

## 秩的等价刻画

以下说法对任意矩阵 $A\\in\\mathbb{R}^{m\\times n}$ 都等价地给出同一个数
$r=\\operatorname{rank}(A)$：

  - 线性无关的**列**的最大个数（列秩），也等于线性无关的**行**的最大个数（行秩）
  - 化为行阶梯形后非零行（主元）的个数
  - 列空间（像空间）的维数 $\\dim\\operatorname{Col}(A)$
  - 非零奇异值的个数（见 [SVD](/0012_线性代数_SVD)）
  - 最大的非零子式的阶数

其中：$r\\le\\min(m,n)$；当 $r=\\min(m,n)$ 时称为**满秩**，否则称为**降秩（秩亏）**。

## 秩与线性方程组

对方程组 $A\\mathbf{x}=\\mathbf{b}$，记增广矩阵 $\[A\\mid\\mathbf{b}\]$，则：

| 条件                                                                       | 解的情况                                     |
| ------------------------------------------------------------------------ | ---------------------------------------- |
| $\\operatorname{rank}(A)\<\\operatorname{rank}(\[A\\mid\\mathbf{b}\])$   | 无解                                       |
| $\\operatorname{rank}(A)=\\operatorname{rank}(\[A\\mid\\mathbf{b}\])=n$  | 唯一解                                      |
| $\\operatorname{rank}(A)=\\operatorname{rank}(\[A\\mid\\mathbf{b}\])\<n$ | 无穷多解，自由变量个数为 $n-\\operatorname{rank}(A)$ |

表中：$n$ 为未知数个数；对比结论：秩决定了方程组是否有解以及解的自由度，详见 [线性方程组](/0035_线性代数_线性方程组)。

## 更多性质

  - $\\operatorname{rank}(A+B)\\le\\operatorname{rank}(A)+\\operatorname{rank}(B)$
  - $\\operatorname{rank}(A^{T}A)=\\operatorname{rank}(AA^{T})=\\operatorname{rank}(A)$，这保证了最小二乘的正规方程在
    $A$ 列满秩时有唯一解
  - 左乘或右乘可逆矩阵不改变秩：$\\operatorname{rank}(PAQ)=\\operatorname{rank}(A)$（$P,Q$
    可逆），所以初等变换不改变秩
  - 秩 1 矩阵可以写成外积形式：$A=uv^{T}$

## 低秩近似

秩越低，矩阵的信息越「冗余」，可以用更少的参数表示。给定目标秩 $k$，Frobenius 范数意义下的最佳近似由截断 SVD
给出（Eckart–Young 定理）：

$$ A\_k=\\sum\_{i=1}^{k}\\sigma\_i,u\_iv\_i^{T},\\qquad
\\min\_{\\operatorname{rank}(B)\\le k}\\lVert
A-B\\rVert\_F=\\Bigl(\\sum\_{i\>k}\\sigma\_i^{2}\\Bigr)^{1/2} $$

其中：

  - $\\sigma\_i$：第 $i$ 大的奇异值；$u\_i,v\_i$：对应的左、右奇异向量
  - $A\_k$：保留前 $k$ 个奇异值得到的秩 $k$ 矩阵；误差由被丢弃的奇异值决定
  - 参数量：$m\\times n$ 矩阵需要 $mn$ 个数，秩 $k$ 近似只需要约 $k(m+n)$ 个

## 在机器学习中的作用

  - LoRA 等参数高效微调：假设权重的更新量是低秩的，用 $\\Delta W=BA$（秩 $r\\ll\\min(m,n)$）近似
  - 推荐系统：用户-物品评分矩阵的低秩分解（矩阵分解）
  - PCA：数据矩阵的有效秩对应主成分的个数，见 [PCA](/0046_线性代数_PCA)
  - 数值秩：实际计算中奇异值小于阈值就视为 0，所以浮点计算里「秩」要看奇异值而不是严格为 0

## 常见误区

  - 行列式为 0 只能说明方阵降秩，不能说明降了多少；要知道秩需要初等变换或 SVD
  - 秩不是「非零元素的个数」；稀疏矩阵可以是满秩的，稠密矩阵也可以是低秩的
  - 数值上「很接近降秩」（病态）和「真的降秩」不同，见 [范数与条件数](/0045_线性代数_Matrix_范数与条件数)

## 相关文章

  - [向量空间](/0034_线性代数_向量空间)：列空间、行空间、零空间与秩的关系
  - [初等变换](/0038_线性代数_Matrix_初等变换)：行阶梯形中主元个数即为秩
  - [线性方程组](/0035_线性代数_线性方程组)：$\\operatorname{rank}(A)$ 与
    $\\operatorname{rank}(\[A\\mid\\mathbf{b}\])$ 决定解的情况
  - [线性变换](/0039_线性代数_线性变换)：秩是像空间的维数
  - [SVD](/0012_线性代数_SVD)：非零奇异值的个数等于秩
