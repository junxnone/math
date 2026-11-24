-----

| Title     | 线性代数 Matrix 秩                                      |
| --------- | -------------------------------------------------- |
| Created @ | `2025-01-14T08:09:57Z`                             |
| Updated @ | `2026-11-24T14:43:13Z`                             |
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

## 相关文章

  - [向量空间](https://github.com/junxnone/math/issues/34)：列空间、行空间、零空间与秩的关系
  - [初等变换](https://github.com/junxnone/math/issues/38)：行阶梯形中主元个数即为秩
  - [线性方程组](https://github.com/junxnone/math/issues/35)：$\\operatorname{rank}(A)$
    与 $\\operatorname{rank}(\[A\\mid\\mathbf{b}\])$ 决定解的情况
  - [线性变换](https://github.com/junxnone/math/issues/39)：秩是像空间的维数
  - [SVD](https://github.com/junxnone/math/issues/12)：非零奇异值的个数等于秩
