-----

| Title     | 线性代数 Matrix 矩阵乘积                                   |
| --------- | -------------------------------------------------- |
| Created @ | `2025-01-14T07:02:28Z`                             |
| Updated @ | `2025-01-14T07:02:28Z`                             |
| Labels    | \`\`                                               |
| Edit @    | [here](https://github.com/junxnone/math/issues/27) |

-----

# 矩阵乘积

  - **Matrix Product**
  - $C = AB$
      - 矩阵 A 的列数必须和矩 阵 B 的行数相等。
      - $C\_{ij}=\\sum\_{k}A\_{ik}B\_{k j}$

## 乘积性质

  - **交换律:** $A \\circ B = B \\circ A$ 的情况并非总是满足
  - **结合律:** $A \\circ (B \\circ C) = (A \\circ B) \\circ C$
  - **分配律:** $A \\circ (B + C) = A \\circ B + A \\circ C$

## 例子

$$A=\\begin{pmatrix} a\_{11} & a\_{12} & \\cdots & a\_{1n}\\ a\_{21} &
a\_{22} & \\cdots & a\_{2n}\\ \\vdots & \\vdots & \\ddots & \\vdots\\
a\_{m1} & a\_{m2} & \\cdots & a\_{mn} \\end{pmatrix}$$

$$B=\\begin{pmatrix} b\_{11} & b\_{12} & \\cdots & b\_{1k}\\ b\_{21} &
b\_{22} & \\cdots & b\_{2k}\\ \\vdots & \\vdots & \\ddots & \\vdots\\
b\_{n1} & b\_{n2} & \\cdots & b\_{nk} \\end{pmatrix}$$

$$C=\\begin{pmatrix} c\_{11} & c\_{12} & \\cdots & c\_{1k}\\ c\_{21} &
c\_{22} & \\cdots & c\_{2k}\\ \\vdots & \\vdots & \\ddots & \\vdots\\
c\_{m1} & c\_{m2} & \\cdots & c\_{mk} \\end{pmatrix}$$

$c\_{ik}=\\sum\_{j = 1}^{n}a\_{ij}b\_{jk}$

$c\_{11}=a\_{11}b\_{11}+a\_{12}b\_{21}+\\cdots + a\_{1n}b\_{n1}$

$c\_{12}=a\_{11}b\_{12}+a\_{12}b\_{22}+\\cdots + a\_{1n}b\_{n2}$

$\\cdots$

$c\_{1k}=a\_{11}b\_{1k}+a\_{12}b\_{2k}+\\cdots + a\_{1n}b\_{nk}$

$c\_{21}=a\_{21}b\_{11}+a\_{22}b\_{21}+\\cdots + a\_{2n}b\_{n1}$

$c\_{22}=a\_{21}b\_{12}+a\_{22}b\_{22}+\\cdots + a\_{2n}b\_{n2}$

$\\cdots$

$c\_{2k}=a\_{21}b\_{1k}+a\_{22}b\_{2k}+\\cdots + a\_{2n}b\_{nk}$

$\\cdots$

$c\_{m1}=a\_{m1}b\_{11}+a\_{m2}b\_{21}+\\cdots + a\_{mn}b\_{n1}$

$c\_{m2}=a\_{m1}b\_{12}+a\_{m2}b\_{22}+\\cdots + a\_{mn}b\_{n2}$

$\\cdots$

$c\_{mk}=a\_{m1}b\_{1k}+a\_{m2}b\_{2k}+\\cdots + a\_{mn}b\_{nk}$
