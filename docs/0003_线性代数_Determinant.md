---
Title | 线性代数 Determinant
-- | --
Created @ | `2022-03-19T09:29:27Z`
Updated @| `2026-11-27T01:33:15Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/3)

---
# Determinant  行列式

- 行列式 - `determinant` - `det(A)` - `|A|`
- 只对**方阵**定义，把一个 $n$ 阶方阵映射成一个数

$$ D = \begin{vmatrix}
a_{11} & a_{12} & ... & a_{1n} \
a_{21} & a_{22} & ... & a_{2n} \
... & ... & ... & ... \
a_{n1} & a_{n2} & ... & a_{nn} \
\end{vmatrix}$$

## 几何意义

- 行列式的绝对值 $\lvert\det A\rvert$ 是 $A$ 所代表的线性变换对**面积（二维）/ 体积（三维）的缩放倍数**：以 $A$ 的列向量为棱的平行四边形 / 平行六面体的面积 / 体积
- 符号表示方向：$\det A>0$ 保持定向（不翻转），$\det A<0$ 翻转定向（含一次镜像）
- $\det A=0$ 表示变换把空间压缩到低维（面积 / 体积为 0），此时 $A$ 不可逆

## 定义（逆序数法）

$$
\det A=\sum_{\sigma\in S_n}\operatorname{sgn}(\sigma)\prod_{i=1}^{n}a_{i,\sigma(i)}
$$

其中：

- $S_n$：$1,2,\dots,n$ 的全部 $n!$ 个排列；$\sigma$：其中一个排列，$\sigma(i)$ 表示第 $i$ 行选取的列号
- $\operatorname{sgn}(\sigma)=(-1)^{\tau(\sigma)}$：排列的符号，$\tau(\sigma)$ 为逆序数（排列中「大数在前、小数在后」的数对个数）
- 含义：从每行每列各取一个元素相乘，所有取法的乘积按符号求和；共 $n!$ 项，所以直接用定义计算量很大

## 行列式计算

### 对角线法
- 适用于 二三阶行列式(更高阶行列式不符合规律)

#### 二阶行列式
$$ D_2 = \begin{vmatrix}
a_{11} & a_{12} \
a_{21} & a_{22} \
\end{vmatrix}$$

$ D_2 = a_{11}a_{22} - a_{12}a_{21}$

#### 三阶行列式

$$ D_3 = \begin{vmatrix}
a_{11} & a_{12} & a_{13} \
a_{21} & a_{22} & a_{23} \
a_{31} & a_{32} & a_{33} \
\end{vmatrix}$$

- 红色对角线 相乘 **取正**
- 蓝色对角线 相乘 **取负**

$$ \begin{vmatrix}
{\color{Red} a_{11}} & {\color{Red} a_{12}} & {\color{Red} a_{13}} \
a_{21} & {\color{Red} a_{22}} & {\color{Red} a_{23}} \
a_{31} & a_{32} & {\color{Red} a_{33}} \
\end{vmatrix}\begin{vmatrix}
a_{11} & a_{12} \
{\color{Red} a_{21}} & a_{22} \
{\color{Red} a_{31}} & {\color{Red} a_{32}} \
\end{vmatrix}$$

$$ \begin{vmatrix}
a_{11} & a_{12} & {\color{Blue} a_{13}} \
a_{21} & {\color{Blue} a_{22}} & {\color{Blue} a_{23}} \
{\color{Blue} a_{31}} & {\color{Blue} a_{32}} & {\color{Blue} a_{33}} \
\end{vmatrix}\begin{vmatrix}
{\color{Blue} a_{11}} & {\color{Blue} a_{12}} \
{\color{Blue} a_{21}} & a_{22} \
a_{31} & a_{32} \
\end{vmatrix}$$

$$D_3 = {\color{Red} a_{11}a_{22}a_{33} + a_{12}a_{23}a_{31} + a_{13}a_{21}a_{32}}{\color{Blue} -a_{13}a_{22}a_{31}-a_{11}a_{23}a_{32}-a_{12}a_{21}a_{33}}$$

### 代数余子式法

$$ D_{nn} = \begin{vmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \
a_{21} & a_{22} & \cdots & a_{2n} \
\vdots  & \vdots & \vdots & \vdots \
a_{n1} & a_{n2} & \cdots & a_{nn} \
\end{vmatrix}$$

$$D_{nn} = (-1)^{1+1}a_{11}M_{11} + (-1)^{1+2}a_{12}M_{12} + ... $$
$$+ (-1)^{i+j}a_{ij}M_{ij} + ... + (-1)^{n+n}a_{nn}M_{nn}$$

其中：

- $M_{ij}$：**余子式**，删除第 $i$ 行第 $j$ 列后剩下的 $n-1$ 阶子矩阵的行列式
- $A_{ij}=(-1)^{i+j}M_{ij}$：**代数余子式**；上式即按第 1 行展开 $D=\sum_j a_{1j}A_{1j}$，也可以按任意行或列展开，选含 0 最多的行（列）最省事

$$ M_{12} = \begin{vmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \
{\color{Red} a_{21}} & a_{22} & {\color{Red} \cdots} & {\color{Red} a_{2n}} \
{\color{Red} \vdots}  & \vdots & {\color{Red} \vdots} & {\color{Red} \vdots} \
{\color{Red} a_{n1}} & a_{n2} & {\color{Red} \cdots} & {\color{Red} a_{nn}} \
\end{vmatrix}
= \begin{vmatrix}
a_{21} & a_{23} & \cdots & a_{2n} \
a_{31} & a_{33} & \cdots & a_{3n} \
\vdots  & \vdots & \vdots & \vdots \
a_{n1} & a_{n3} & \cdots & a_{nn} \
\end{vmatrix}$$

> $M_{ij}$ 为 矩阵 删除 $a_{ij}$ 所在行列后剩余的部分组成的矩阵的行列式

#### D3 Examples

$$ D_3 = \begin{vmatrix}
a_{11} & a_{12} & a_{13} \
a_{21} & a_{22} & a_{23} \
a_{31} & a_{32} & a_{33} \
\end{vmatrix}$$

$D_3 = (-1)^{1+1}a_{11}M_{11} + (-1)^{1+2}a_{12}M_{12} + (-1)^{1+3}a_{13}M_{13}$

$$ M_{11} = \begin{vmatrix}
a_{22} & a_{23} \
a_{32} & a_{33} \
\end{vmatrix}$$

### 等价转换法
- 行列式性质
  - 行列式的某一行（列）的各元素乘同一数然后加到另一行（列）对应的元素上去, **行列式不变**
  - 行列式中某一行（列）的所有元素的公因子可以提到行列式记号的外面
- **核心思想: 将行列式转化成上三角行列式**，上三角（或下三角）行列式的值等于主对角线元素之积

#### D4 Examples

$$ D_4 = \begin{vmatrix}
3 & 1 & 1 & 1 \
1 & 3 & 1 & 1 \
1 & 1 & 3 & 1 \
1 & 1 & 1 & 3 \
\end{vmatrix}$$

$$ \overrightarrow{r1=r1+r2+r3+r4}
= \begin{vmatrix}
6 & 6 & 6 & 6 \
1 & 3 & 1 & 1 \
1 & 1 & 3 & 1 \
1 & 1 & 1 & 3 \
\end{vmatrix}$$

$$ \overrightarrow{r1=r1\div 6}
= 6\begin{vmatrix}
1 & 1 & 1 & 1 \
1 & 3 & 1 & 1 \
1 & 1 & 3 & 1 \
1 & 1 & 1 & 3 \
\end{vmatrix}$$  

$$ \overrightarrow{r2=r2-r1,r3=r3-r1,r4=r4-r1}$$ 
$$ = 6\begin{vmatrix}
1 & 1 & 1 & 1 \
0 & 2 & 0 & 0 \
0 & 0 & 2 & 0 \
0 & 0 & 0 & 2 \
\end{vmatrix}$$ 

$$ = 6 \times (1 \times 2 \times 2 \times 2) = 48$$

> 原文档此例最后一行写作 `1 1 3 3`，会使第一步的列和不相等；已改为 `1 1 1 3`，结果 $48$ 不变。

## 方法对比

| 方法 | 适用 | 计算量 |
| --- | --- | --- |
| 对角线法 | 2、3 阶 | 常数 |
| 代数余子式展开 | 含大量 0 的行或列 | 一般为 $O(n!)$ |
| 等价转换（高斯消元） | 一般矩阵，数值计算 | $O(n^3)$ |
| 逆序数定义 | 理论推导 | $O(n!\cdot n)$ |

表中：对比结论：手算低阶用对角线法或展开，一般和数值计算都用化成三角形的消元法。

## 性质

| 性质 | 表达式 |
| --- | --- |
| 转置不变 | $\det A^{T}=\det A$ |
| 乘积 | $\det(AB)=\det A\cdot\det B$ |
| 逆 | $\det A^{-1}=1/\det A$ |
| 数乘 | $\det(kA)=k^{n}\det A$（$n$ 阶） |
| 交换两行（列） | 行列式变号 |
| 两行（列）成比例或某行为 0 | 行列式为 0 |
| 与特征值 | $\det A=\prod_i\lambda_i$（特征值之积）；$\operatorname{tr}A=\sum_i\lambda_i$ |

表中：对比结论：行列式与特征值、可逆性、秩紧密相关，见 [特征值与特征向量](https://github.com/junxnone/math/issues/36)、[矩阵的逆](https://github.com/junxnone/math/issues/31)、[矩阵的秩](https://github.com/junxnone/math/issues/29)。

## 克莱姆法则

对 $n$ 个方程 $n$ 个未知数的方程组 $A\mathbf{x}=\mathbf{b}$，当 $\det A\ne0$ 时，

$$
x_j=\frac{\det A_j}{\det A}
$$

其中：$A_j$ 是把 $A$ 的第 $j$ 列换成 $\mathbf{b}$ 得到的矩阵。克莱姆法则理论上优美，但计算量大，实际求解用消元或矩阵分解。

## 在机器学习中的作用

- 多元高斯分布的归一化常数含 $\det\Sigma$；$\log\det$ 衡量分布的「体积」
- 变量替换公式中的雅可比行列式，见 [雅可比矩阵](https://github.com/junxnone/math/issues/44)、[重积分](https://github.com/junxnone/math/issues/55)
- 判断协方差 / Hessian 矩阵是否奇异、是否正定，见 [对称正定与二次型](https://github.com/junxnone/math/issues/41)

## 常见误区

- $\det(A+B)\ne\det A+\det B$，行列式不是线性的（只对单独一行或一列线性）
- $\det(kA)=k^{n}\det A$，不是 $k\det A$
- 行列式「很小」不一定表示接近奇异（取决于尺度），判断数值奇异性要看条件数，见 [范数与条件数](https://github.com/junxnone/math/issues/45)


