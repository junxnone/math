-----

| Title     | 线性代数 Matrix 逆                                      |
| --------- | -------------------------------------------------- |
| Created @ | `2025-01-14T08:20:42Z`                             |
| Updated @ | `2025-01-14T08:20:42Z`                             |
| Labels    | \`\`                                               |
| Edit @    | [here](https://github.com/junxnone/math/issues/31) |

-----

# 矩阵的逆

  - **矩阵逆**: $AA^{-1}=A^{-1}A=E$
      - 对于一个 n 阶方阵 A, 如果存在另一个 n 阶方阵 B 满足 $AB=BA=E$, E 为单位矩阵
      - 即 $B=A^{-1}$
      - A B 互为逆矩阵

## 性质

  - 若 $A$ 可逆，则 $A^{-1}$ 也可逆，且 $(A^{-1})^{-1}=A$ 。这就好比一个数 $x\\neq0$ ，它的倒数
    $\\frac{1}{x}$ 的倒数就是 $x$ 自身。
  - 若 $A$ 可逆， $k\\neq0$ 为常数，则 $(kA)^{-1}=\\frac{1}{k}A^{-1}$ 。
  - 若 $A$ 、 $B$ 是同阶可逆矩阵，则 $(AB)^{-1}=B^{-1}A^{-1}$ 。

## 求逆矩阵的方法

### 伴随矩阵法

  - 对于 $n$ 阶方阵 $A$ ，其逆矩阵 $A^{-1}=\\frac{1}{\\vert A\\vert}adj(A)$ ，其中
    $\\vert A\\vert$ 是 $A$ 的行列式， $adj(A)$ 是 $A$ 的伴随矩阵。伴随矩阵 $adj(A)$ 的元素是
    $A$ 的代数余子式构成的转置矩阵。
  - 例如，对于 $2\\times2$ 矩阵

$$A = \\begin{pmatrix}a\&b\\ c\&d\\end{pmatrix}$$

$$\\vert A\\vert=ad - bc$$

其伴随矩阵

$$adj(A)=\\begin{pmatrix}d&-b\\ -c\&a\\end{pmatrix}$$

当 $\\vert A\\vert\\neq0$ 时

$$A^{-1}=\\frac{1}{ad - bc}\\begin{pmatrix}d&-b\\ -c\&a\\end{pmatrix}$$

### 初等变换法

  - 将矩阵 $A$ 和单位矩阵 $I$ 拼成一个 $n\\times2n$ 的矩阵 $(A|I)$ ，然后对这个矩阵进行初等行变换，当左边的
    $A$ 变成单位矩阵 $I$ 时，右边的 $I$ 就变成了 $A^{-1}$ 。
  - 例如，对于矩阵

$$A=\\begin{pmatrix}1&2\\ 3&4\\end{pmatrix}$$

构造

$$(A|I)=\\begin{pmatrix}1&2&1&0\\ 3&4&0&1\\end{pmatrix}$$

第一行乘以 $- 3$ 加到第二行得到

$$\\begin{pmatrix}1&2&1&0\\ 0&-2&-3&1\\end{pmatrix}$$

第二行乘以 $-\\frac{1}{2}$ 得到

$$\\begin{pmatrix}1&2&1&0\\
0&1&\\frac{3}{2}&-\\frac{1}{2}\\end{pmatrix}$$

第一行减去第二行的 $2$ 倍得到

$$\\begin{pmatrix}1&0&-2&1\\
0&1&\\frac{3}{2}&-\\frac{1}{2}\\end{pmatrix}$$

所以

$$A^{-1}=\\begin{pmatrix}-2&1\\
\\frac{3}{2}&-\\frac{1}{2}\\end{pmatrix}$$

## 应用

  - 在线性方程组 $Ax = b$ （ $A$ 是 $n$ 阶方阵， $x$ 和 $b$ 是 $n$ 维向量）中，如果 $A$
    可逆，那么方程组的解为 $x = A^{-1}b$ 。这为求解线性方程组提供了一种有效的方法。
