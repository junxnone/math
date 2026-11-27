-----

| Title     | 线性代数 Matrix 矩阵乘积                                   |
| --------- | -------------------------------------------------- |
| Created @ | `2025-01-14T07:02:28Z`                             |
| Updated @ | `2026-11-27T01:33:03Z`                             |
| Labels    | \`\`                                               |
| Edit @    | [here](https://github.com/junxnone/math/issues/27) |

-----

# 矩阵乘积

  - **Matrix Product**
  - $C = AB$
      - 矩阵 A 的列数必须和矩 阵 B 的行数相等。
      - $C\_{ij}=\\sum\_{k}A\_{ik}B\_{k j}$

其中：

  - $A$：$m\\times n$ 矩阵；$B$：$n\\times p$ 矩阵；乘积 $C=AB$ 是 $m\\times p$
    矩阵（内部维度 $n$ 必须相同，乘完消失）
  - $C\_{ij}$：$C$ 的第 $i$ 行第 $j$ 列元素，等于 $A$ 的第 $i$ 行与 $B$ 的第 $j$ 列的点乘

## 乘积性质

  - **交换律:** 一般**不成立**：$AB\\ne BA$（甚至 $AB$ 有定义时 $BA$ 可能没有定义）
  - **结合律:** $(AB)C = A(BC)$
  - **分配律:** $A(B + C) = AB + AC$，$(A+B)C=AC+BC$
  - **转置：** $(AB)^T=B^TA^T$；**逆：** 若 $A,B$ 可逆，$(AB)^{-1}=B^{-1}A^{-1}$
  - **单位元：** $AI=IA=A$

> 原文档此处误用了 $\\circ$ 符号（$\\circ$ 通常表示哈达玛积，见
> [哈达玛乘积](https://github.com/junxnone/math/issues/28)），这里已改为普通乘积。

## 例子

$$A=\\begin{pmatrix} a\_{11} & a\_{12} & \\cdots & a\_{1n}  
a\_{21} & a\_{22} & \\cdots & a\_{2n}  
\\vdots & \\vdots & \\ddots & \\vdots  
a\_{m1} & a\_{m2} & \\cdots & a\_{mn} \\end{pmatrix}$$

$$B=\\begin{pmatrix} b\_{11} & b\_{12} & \\cdots & b\_{1k}  
b\_{21} & b\_{22} & \\cdots & b\_{2k}  
\\vdots & \\vdots & \\ddots & \\vdots  
b\_{n1} & b\_{n2} & \\cdots & b\_{nk} \\end{pmatrix}$$

$$C=\\begin{pmatrix} c\_{11} & c\_{12} & \\cdots & c\_{1k}  
c\_{21} & c\_{22} & \\cdots & c\_{2k}  
\\vdots & \\vdots & \\ddots & \\vdots  
c\_{m1} & c\_{m2} & \\cdots & c\_{mk} \\end{pmatrix}$$

$c\_{ik}=\\sum\_{j = 1}^{n}a\_{ij}b\_{jk}$

$c\_{11}=a\_{11}b\_{11}+a\_{12}b\_{21}+\\cdots + a\_{1n}b\_{n1}$

数值例：

$$
\\begin{bmatrix}1&2\\3&4\\end{bmatrix}\\begin{bmatrix}0&1\\1&0\\end{bmatrix}=\\begin{bmatrix}2&1\\4&3\\end{bmatrix},\\qquad
\\begin{bmatrix}0&1\\1&0\\end{bmatrix}\\begin{bmatrix}1&2\\3&4\\end{bmatrix}=\\begin{bmatrix}3&4\\1&2\\end{bmatrix}
$$

两个结果不同，说明 $AB\\ne BA$：右乘置换矩阵交换**列**，左乘交换**行**。

## 三种理解方式

``` mermaid
flowchart LR
    A[AB] --> P1[元素视角 行点乘列]
    A --> P2[列视角 AB 的每一列是 A 的列的线性组合]
    A --> P3[行视角 AB 的每一行是 B 的行的线性组合]
    A --> P4[外积视角 AB 是若干秩 1 矩阵之和]
```

图中：同一个乘积可以从四个角度理解，在不同场景选最方便的一个。

  - 列视角：$AB$ 的第 $j$ 列 $=A,b\_j$，即用 $B$ 的第 $j$ 列作系数，对 $A$ 的各列做线性组合
  - 行视角：$AB$ 的第 $i$ 行 $=a\_i^{T}B$
  - 外积视角：

$$ AB=\\sum\_{k=1}^{n}a\_{:k},b\_{k:}^{T} $$

其中：$a\_{:k}$ 是 $A$ 的第 $k$ 列，$b\_{k:}^{T}$ 是 $B$ 的第 $k$ 行；每一项是一个秩为 1 的
$m\\times p$ 矩阵，$n$ 项相加得到 $AB$。

## 与线性变换、特殊矩阵

  - 矩阵是线性变换的表示，$AB$ 对应「先作用 $B$，再作用 $A$」的**复合变换**，所以顺序不能交换，见
    [线性变换](https://github.com/junxnone/math/issues/39)
  - 对角矩阵左乘缩放行，右乘缩放列；单位矩阵是乘法的单位元；正交矩阵相乘仍是正交矩阵

## 计算量

用定义计算 $m\\times n$ 与 $n\\times p$ 的乘积，需要 $mnp$ 次乘法和约同样多次加法，即 $O(mnp)$；方阵
$n\\times n$ 为 $O(n^3)$（Strassen 等算法可降到更低的指数）。矩阵乘法是深度学习计算量的主要来源。

## 与相关运算对比

| 运算    | 符号            | 形状要求              | 结果                                                                   |
| ----- | ------------- | ----------------- | -------------------------------------------------------------------- |
| 矩阵乘积  | $AB$          | $A$ 的列数 = $B$ 的行数 | $m\\times p$                                                         |
| 哈达玛积  | $A\\circ B$   | 两者同形              | 同形，逐元素相乘，见 [哈达玛乘积](https://github.com/junxnone/math/issues/28)       |
| 克罗内克积 | $A\\otimes B$ | 任意                | $mp\\times nq$，见 [克罗内克积](https://github.com/junxnone/math/issues/26) |

表中：对比结论：三种「乘积」含义完全不同，使用时要看清符号。

## 相关文章

  - [矩阵](https://github.com/junxnone/math/issues/4)、[转置](https://github.com/junxnone/math/issues/30)、[矩阵的逆](https://github.com/junxnone/math/issues/31)、[线性变换](https://github.com/junxnone/math/issues/39)
