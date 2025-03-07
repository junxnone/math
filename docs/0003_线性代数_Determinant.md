---
Title | 线性代数 Determinant
-- | --
Created @ | `2022-03-19T09:29:27Z`
Updated @| `2025-01-14T06:23:05Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/3)

---
# Determinant  行列式


- 行列式 - `determinant` - `det(A)` - `|A|`

$$\huge D = \begin{vmatrix}
a_{11} & a_{12} & ... & a_{1n} \\
a_{21} & a_{22} & ... & a_{2n} \\
... & ... & ... & ... \\
a_{n1} & a_{n2} & ... & a_{nn} \\
\end{vmatrix}$$


## 行列式计算


### 对角线法
- 适用于 二三阶行列式(更高阶行列式不符合规律)

#### 二阶行列式
$$\huge D_2 = \begin{vmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22} \\
\end{vmatrix}$$

$\huge D_2 = a_{11}a_{22} - a_{12}a_{21}$

#### 三阶行列式

$$\huge D_3 = \begin{vmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33} \\
\end{vmatrix}$$

- 红色对角线 相乘 **取正**
- 蓝色对角线 相乘 **取负**

$$\huge \begin{vmatrix}
{\color{Red} a_{11}} & {\color{Red} a_{12}} & {\color{Red} a_{13}} \\
a_{21} & {\color{Red} a_{22}} & {\color{Red} a_{23}} \\
a_{31} & a_{32} & {\color{Red} a_{33}} \\
\end{vmatrix}\begin{vmatrix}
a_{11} & a_{12} \\
{\color{Red} a_{21}} & a_{22} \\
{\color{Red} a_{31}} & {\color{Red} a_{32}} \\
\end{vmatrix}$$

$$\huge \begin{vmatrix}
a_{11} & a_{12} & {\color{Blue} a_{13}} \\
a_{21} & {\color{Blue} a_{22}} & {\color{Blue} a_{23}} \\
{\color{Blue} a_{31}} & {\color{Blue} a_{32}} & {\color{Blue} a_{33}} \\
\end{vmatrix}\begin{vmatrix}
{\color{Blue} a_{11}{\color{Blue} }} & {\color{Blue} a_{12}} \\
{\color{Blue} a_{21}} & a_{22} \\
a_{31} & a_{32} \\
\end{vmatrix}$$

$$D_3 = {\color{Red} a_{11}a_{22}a_{33} + a_{12}a_{23}a_{31} + a_{13}a_{21}a_{32}}{\color{Blue} -a_{13}a_{22}a_{31}-a_{11}a_{23}a_{32}-a_{12}a_{21}a_{33}}$$

### 代数余子式法

$$\huge D_{nn} = \begin{vmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots  & \vdots & \vdots & \vdots \\
a_{n1} & a_{n2} & \cdots & a_{nn} \\
\end{vmatrix}$$

$$D_{nn} = (-1)^{1+1}a_{11}M_{11} + (-1)^{1+2}a_{12}M_{12} + ... $$
$$+ (-1)^{i+j}a_{ij}M_{ij} + ... + (-1)^{n+n}a_{nn}M_{nn}$$

$$\large M_{12} = \begin{vmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
{\color{Red} a_{21}} & a_{22} & {\color{Red} \cdots} & {\color{Red} a_{2n}} \\
{\color{Red} \vdots}  & \vdots & {\color{Red} \vdots} & {\color{Red} \vdots} \\
{\color{Red} a_{n1}} & a_{n2} & {\color{Red} \cdots} & {\color{Red} a_{nn}} \\
\end{vmatrix}
= \begin{vmatrix}
a_{21} & a_{23} & \cdots & a_{2n} \\
a_{31} & a_{33} & \cdots & a_{3n} \\
\vdots  & \vdots & \vdots & \vdots \\
a_{n1} & a_{n3} & \cdots & a_{nn} \\
\end{vmatrix}$$


> $M_{ij}$ 为 矩阵 删除 $a_{ij} 所在行列后剩余的部分组成的矩阵$

#### D3 Examples

$$\huge D_3 = \begin{vmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33} \\
\end{vmatrix}$$

$D_3 = (-1)^{1+1}a_{11}M_{11} + (-1)^{1+2}a_{12}M_{12} + ... + (-1)^{3+1}a_{31}M_{31}$

$$\huge M_{11} = \begin{vmatrix}
a_{22} & a_{23} \\
a_{32} & a_{33} \\
\end{vmatrix}$$

### 等价转换法
- 行列式性质
  - 行列式的某一行（列）的各元素乘同一数然后加到另一行（列）对应的元素上去, **行列式不变**
  - 行列式中某一行（列）的所有元素的公因子可以提到行列式记号的外面
- **核心思想: 将行列式转化成上三角行列式**

#### D4 Examples


$$\huge D_4 = \begin{vmatrix}
3 & 1 & 1 & 1 \\
1 & 3 & 1 & 1 \\
1 & 1 & 3 & 1 \\
1 & 1 & 3 & 3 \\
\end{vmatrix}$$

$$\huge \overrightarrow{r1=r1+r2+r3+r4}
= \begin{vmatrix}
6 & 6 & 6 & 6 \\
1 & 3 & 1 & 1 \\
1 & 1 & 3 & 1 \\
1 & 1 & 3 & 3 \\
\end{vmatrix}$$

$$\huge \overrightarrow{r1=r1\div 6}
= 6\begin{vmatrix}
1 & 1 & 1 & 1 \\
1 & 3 & 1 & 1 \\
1 & 1 & 3 & 1 \\
1 & 1 & 3 & 3 \\
\end{vmatrix}$$  

$$\huge \overrightarrow{r2=r2-r1,r3=r3-r1,r4=r4-r1}$$ 
$$\huge = 6\begin{vmatrix}
1 & 1 & 1 & 1 \\
0 & 2 & 0 & 0 \\
0 & 0 & 2 & 0 \\
0 & 0 & 0 & 2 \\
\end{vmatrix}$$ 

$$\huge = 6 \times (1 \times 2 \times 2 \times 2) = 48$$

### 逆序数法

## Reference


