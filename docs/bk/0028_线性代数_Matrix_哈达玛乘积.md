-----

| Title     | 线性代数 Matrix 哈达玛乘积                                  |
| --------- | -------------------------------------------------- |
| Created @ | `2025-01-14T07:04:52Z`                             |
| Updated @ | `2025-01-14T07:04:52Z`                             |
| Labels    | \`\`                                               |
| Edit @    | [here](https://github.com/junxnone/math/issues/28) |

-----

# 哈达玛乘积

  - **Hadamard Product**/**Element-Wise Product**

## 性质

  - **交换律:** $A \\circ B = B \\circ A$
  - **结合律:** $A \\circ (B \\circ C) = (A \\circ B) \\circ C$
  - **分配律:** $A \\circ (B + C) = A \\circ B + A \\circ C$

> $\\circ$ 与 $\\odot$ 都可以表示点积

## 例子

$$\\left\[ \\begin{array}{ccc}  
a\_{11} & a\_{12} & a\_{13}\\ a\_{21} & a\_{22} & a\_{23}\\ a\_{31} &
a\_{32} & a\_{33} \\end{array} \\right\] \\circ \\left\[
\\begin{array}{ccc} b\_{11} & b\_{12} & b\_{13}\\ b\_{21} & b\_{22} &
b\_{23}\\ b\_{31} & b\_{32} & b\_{33} \\end{array} \\right\] = \\left\[
\\begin{array}{ccc} a\_{11}\\times b\_{11} & a\_{12}\\times b\_{12} &
a\_{13}\\times b\_{13}\\ a\_{21}\\times b\_{21} & a\_{22}\\times b\_{22}
& a\_{23}\\times b\_{23}\\ a\_{31}\\times b\_{31} & a\_{32}\\times
b\_{32} & a\_{33}\\times b\_{33} \\end{array} \\right\]$$
