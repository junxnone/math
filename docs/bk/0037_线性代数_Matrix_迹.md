-----

| Title     | 线性代数 Matrix 迹                                      |
| --------- | -------------------------------------------------- |
| Created @ | `2026-11-24T10:06:42Z`                             |
| Updated @ | `2026-11-27T01:42:37Z`                             |
| Labels    | \`\`                                               |
| Edit @    | [here](https://github.com/junxnone/math/issues/37) |

-----

# 矩阵的迹

迹（trace）是方阵主对角线元素之和。它定义简单，却与特征值、范数、矩阵求导紧密相关，在机器学习的公式推导中非常常见。

## 定义

$$ \\operatorname{tr}(A)=\\sum\_{i=1}^{n}a\_{ii} $$

其中：

  - $A\\in\\mathbb{R}^{n\\times n}$：$n$ 阶方阵（迹只对方阵定义）
  - $a\_{ii}$：$A$ 的第 $i$ 个主对角线元素

例：$A=\\begin{bmatrix}1&2\\3&4\\end{bmatrix}$，则
$\\operatorname{tr}(A)=1+4=5$。

## 性质

对适当维度的矩阵 $A,B,C$ 和标量 $c$：

$$ \\begin{aligned}
&\\operatorname{tr}(A+B)=\\operatorname{tr}(A)+\\operatorname{tr}(B),\\qquad
\\operatorname{tr}(cA)=c,\\operatorname{tr}(A)\\
&\\operatorname{tr}(A^\\top)=\\operatorname{tr}(A)\\
&\\operatorname{tr}(AB)=\\operatorname{tr}(BA)\\
&\\operatorname{tr}(ABC)=\\operatorname{tr}(BCA)=\\operatorname{tr}(CAB)
\\end{aligned} $$

其中：

  - 第一行说明迹是线性的
  - 第二行：转置不改变主对角线，所以迹不变
  - 第三行：$A\\in\\mathbb{R}^{m\\times n}$、$B\\in\\mathbb{R}^{n\\times m}$
    时，$AB$ 与 $BA$
    虽然大小不同，迹仍相等；证明：$\\operatorname{tr}(AB)=\\sum\_i\\sum\_j
    a\_{ij}b\_{ji}=\\operatorname{tr}(BA)$
  - 第四行：循环置换不变，但一般不能任意交换顺序，$\\operatorname{tr}(ABC)\\ne\\operatorname{tr}(ACB)$

由 $\\operatorname{tr}(AB)=\\operatorname{tr}(BA)$ 可得**相似不变性**：

$$
\\operatorname{tr}(P^{-1}AP)=\\operatorname{tr}(APP^{-1})=\\operatorname{tr}(A)
$$

其中 $P$ 为任意可逆矩阵。即同一线性变换在不同基下的矩阵有相同的迹，因此迹是线性变换自身的性质，而不依赖坐标选取。

## 与特征值的关系

$$ \\operatorname{tr}(A)=\\sum\_{i=1}^{n}\\lambda\_i $$

其中 $\\lambda\_i$ 是 $A$ 的全部特征值（计重数，见
[特征值与特征向量](/0036_线性代数_特征值与特征向量)）。推导思路：对角化
$A=P\\Lambda P^{-1}$ 后，由相似不变性
$\\operatorname{tr}(A)=\\operatorname{tr}(\\Lambda)=\\sum\\lambda\_i$；对不可对角化的矩阵，通过特征多项式的系数同样成立。

## 与 Frobenius 范数的关系

$$ |A|*F^2=\\sum*{i,j}a\_{ij}^2=\\operatorname{tr}(A^\\top A) $$

其中：

  - $|A|\_F$：Frobenius 范数，把矩阵拉直后的 $L\_2$ 范数（范数见 [norm](/0011_线性代数_norm)）
  - $A\\in\\mathbb{R}^{m\\times n}$：任意矩阵
  - 证明：$(A^\\top A)*{jj}=\\sum\_i a*{ij}^2$，对 $j$ 求和即得
  - 因此 $|A|\_F^2$ 也等于 $A^\\top A$ 的全部特征值之和，即所有奇异值平方和
    $\\sum\_i\\sigma\_i^2$

## 常用的迹技巧

标量等于它自己的迹，所以二次型可以改写成迹的形式，再利用循环性：

$$ \\mathbf{x}^\\top A\\mathbf{x}=\\operatorname{tr}(\\mathbf{x}^\\top
A\\mathbf{x})=\\operatorname{tr}(A\\mathbf{x}\\mathbf{x}^\\top) $$

其中：

  - $\\mathbf{x}\\in\\mathbb{R}^n$：列向量；$A\\in\\mathbb{R}^{n\\times n}$
  - $\\mathbf{x}^\\top A\\mathbf{x}$：一个标量
  - $\\mathbf{x}\\mathbf{x}^\\top$：外积，$n\\times n$ 的矩阵
  - 该技巧常用于把对样本求和的式子转化为协方差矩阵的迹，例如高斯分布的对数似然（见 [Gaussian
    Distribution](/0005_概率论_常见分布_高斯分布进阶)）

迹的常用矩阵求导公式（梯度与 $X$ 同形）：

$$ \\frac{\\partial\\operatorname{tr}(AX)}{\\partial X}=A^\\top,\\qquad
\\frac{\\partial\\operatorname{tr}(X^\\top AX)}{\\partial
X}=(A+A^\\top)X $$

其中 $X$ 是自变量矩阵，$A$ 是与 $X$ 无关的常数矩阵（维度保证乘积有定义）；对称 $A$ 时后式化为 $2AX$。

## 应用

  - 计算矩阵的特征值之和，或检验特征值计算是否正确
  - 损失函数：$|A-B|\_F^2=\\operatorname{tr}\\bigl((A-B)^\\top(A-B)\\bigr)$，用于矩阵逼近与低秩分解
  - 协方差矩阵的迹等于总方差，PCA 中用“保留特征值之和 / 迹”衡量信息保留比例
  - 旋转矩阵 $R$ 的迹与旋转角满足
    $\\operatorname{tr}(R)=1+2\\cos\\theta$（三维），可由旋转矩阵反求旋转角（见
    [Quaternion](/0016_线性代数_线性变换_四元数与三维旋转进阶)）

## Reference

  - [Trace (linear algebra) -
    Wikipedia](https://en.wikipedia.org/wiki/Trace_\(linear_algebra\))
  - The Matrix Cookbook
