-----

| Title     | 线性代数 Matrix 矩阵微积分                                   |
| --------- | --------------------------------------------------- |
| Created @ | `2026-11-27T02:42:51Z`                              |
| Updated @ | `2026-11-27T02:47:35Z`                              |
| Labels    | \`\`                                                |
| Edit @    | [here](https://github.com/junxnone/math/issues/128) |

-----

# 矩阵微积分

矩阵微积分研究**标量、向量、矩阵之间的求导**：损失函数 $\\mathcal{L}(W)$ 对权重矩阵 $W$
的导数怎么算？它是推导线性回归、神经网络反向传播、PCA、高斯分布极大似然等结果的基本工具。基础的多元微分见
[多元函数微分](https://github.com/junxnone/math/issues/54)，雅可比矩阵见
[雅可比矩阵](https://github.com/junxnone/math/issues/44)。

## 概念关系图

``` mermaid
flowchart LR
    S[标量 f] --> G[对向量求导 梯度]
    S --> M[对矩阵求导 与 X 同形]
    V[向量函数 f] --> J[对向量求导 雅可比矩阵]
    G --> H[二阶 Hessian]
    J --> C[链式法则 矩阵乘积]
    M --> T[迹技巧 化简]
```

图中：按「被求导的量」和「对谁求导」分类：标量对向量得到梯度，向量对向量得到雅可比矩阵，标量对矩阵得到同形矩阵；多层复合时使用矩阵形式的链式法则，复杂表达式常借助迹的性质化简。

## 布局约定

对标量 $f$ 与列向量 $\\mathbf{x}\\in\\mathbb{R}^{n}$：

$$ \\frac{\\partial
f}{\\partial\\mathbf{x}}=\\begin{bmatrix}\\dfrac{\\partial f}{\\partial
x\_1}&\\cdots&\\dfrac{\\partial f}{\\partial
x\_n}\\end{bmatrix}^{\\top}\\ \\ (\\text{分母布局，列向量}),\\qquad
\\frac{\\partial
f}{\\partial\\mathbf{x}}=\\begin{bmatrix}\\dfrac{\\partial f}{\\partial
x\_1}&\\cdots&\\dfrac{\\partial f}{\\partial x\_n}\\end{bmatrix}\\ \\
(\\text{分子布局，行向量}) $$

其中：

  - 同一个导数有两种写法，差别只是转置；机器学习中通常采用**分母布局**，即梯度 $\\nabla f$ 与 $\\mathbf{x}$
    同形
  - 对向量函数 $\\mathbf{f}:\\mathbb{R}^n\\to\\mathbb{R}^m$，雅可比矩阵
    $J\_{ij}=\\partial f\_i/\\partial x\_j$ 是 $m\\times n$ 矩阵（分子布局）
  - 使用别人的公式之前必须先确认布局约定，否则结果会差一个转置

## 常用公式

设 $\\mathbf{a},\\mathbf{b},\\mathbf{x}$ 为向量，$A,B,X$ 为矩阵（与求导变量无关的视为常数）：

| 函数                                             | 导数                                     | 说明                                                                                    |
| ---------------------------------------------- | -------------------------------------- | ------------------------------------------------------------------------------------- |
| $\\mathbf{a}^{\\top}\\mathbf{x}$               | $\\mathbf{a}$                          | 线性函数的梯度是系数向量                                                                          |
| $\\mathbf{x}^{\\top}A\\mathbf{x}$              | $(A+A^{\\top})\\mathbf{x}$             | 二次型；$A$ 对称时为 $2A\\mathbf{x}$，见 [对称正定与二次型](https://github.com/junxnone/math/issues/41) |
| $\\lVert\\mathbf{x}\\rVert\_2^2$               | $2\\mathbf{x}$                         | 平方 $L\_2$ 范数，见 [范数](https://github.com/junxnone/math/issues/11)                       |
| $\\lVert A\\mathbf{x}-\\mathbf{b}\\rVert\_2^2$ | $2A^{\\top}(A\\mathbf{x}-\\mathbf{b})$ | 最小二乘目标，令其为 0 得正规方程，见 [最小二乘进阶](https://github.com/junxnone/math/issues/6)              |
| $\\operatorname{tr}(AX)$                       | $A^{\\top}$                            | 迹的线性，见 [矩阵的迹](https://github.com/junxnone/math/issues/37)                             |
| $\\operatorname{tr}(X^{\\top}AX)$              | $(A+A^{\\top})X$                       | 矩阵二次型                                                                                 |
| $\\ln\\lvert\\det X\\rvert$                    | $X^{-\\top}$                           | 高斯分布的对数似然中出现                                                                          |
| $\\det X$                                      | $\\det(X),X^{-\\top}$                  | 行列式的导数                                                                                |

表中：$X^{-\\top}=(X^{-1})^{\\top}$；对比结论：绝大多数公式都可以由「线性」「二次型」「迹」「行列式」这几类基本公式组合得到。

## 链式法则

若 $\\mathbf{y}=\\mathbf{g}(\\mathbf{x})$、$f=h(\\mathbf{y})$，则

$$ \\frac{\\partial
f}{\\partial\\mathbf{x}}=\\Bigl(\\frac{\\partial\\mathbf{y}}{\\partial\\mathbf{x}}\\Bigr)^{\\top}\\frac{\\partial
f}{\\partial\\mathbf{y}}=J\_{g}^{\\top},\\nabla\_{\\mathbf{y}}f $$

其中：$J\_g=\\partial\\mathbf{y}/\\partial\\mathbf{x}$ 是 $\\mathbf{g}$
的雅可比矩阵；上游梯度 $\\nabla\_{\\mathbf{y}}f$ 乘以雅可比矩阵的转置得到对
$\\mathbf{x}$ 的梯度。这正是**反向传播**每一层所做的事：把「损失对输出的梯度」左乘 $J^\\top$ 传到输入，见
[自动微分](https://github.com/junxnone/math/issues/152)。

## 迹技巧

对标量表达式，利用 $\\operatorname{tr}(a)=a$ 与循环不变性
$\\operatorname{tr}(ABC)=\\operatorname{tr}(BCA)$，把变量挪到可以直接套公式的位置：

$$
\\mathbf{x}^{\\top}A\\mathbf{x}=\\operatorname{tr}(A,\\mathbf{x}\\mathbf{x}^{\\top}),\\qquad
df=\\operatorname{tr}\\bigl(G^{\\top}dX\\bigr)\\ \\Longrightarrow\\
\\frac{\\partial f}{\\partial X}=G $$

其中：先对 $f$ 求微分 $df$，把它整理成 $\\operatorname{tr}(G^\\top dX)$ 的形式，则 $G$
就是梯度。这种「微分 + 迹」的方法比逐元素求导高效得多。

## 例：线性回归与高斯 MLE

  - 线性回归：$\\mathcal{L}(\\boldsymbol\\beta)=\\lVert\\mathbf{y}-X\\boldsymbol\\beta\\rVert^2$，$\\nabla\\mathcal{L}=-2X^\\top(\\mathbf{y}-X\\boldsymbol\\beta)$，令为
    0 得 $\\boldsymbol\\beta=(X^\\top X)^{-1}X^\\top\\mathbf{y}$
  - 多元高斯的极大似然：对 $\\ln p=-\\tfrac
    n2\\ln\\lvert\\Sigma\\rvert-\\tfrac12\\sum(\\mathbf{x}\_i-\\boldsymbol\\mu)^\\top\\Sigma^{-1}(\\mathbf{x}\_i-\\boldsymbol\\mu)+C$
    关于 $\\boldsymbol\\mu$、$\\Sigma$ 求导，得到样本均值与样本协方差，见
    [高斯分布进阶](https://github.com/junxnone/math/issues/5)

## 在机器学习中的作用

  - 神经网络的全连接层 $Y=XW$：$\\partial\\mathcal{L}/\\partial
    W=X^{\\top},\\partial\\mathcal{L}/\\partial
    Y$，$\\partial\\mathcal{L}/\\partial
    X=\\partial\\mathcal{L}/\\partial Y;W^{\\top}$
  - 各类矩阵参数模型（PCA、矩阵分解、线性判别）的优化条件都是矩阵导数为零
  - 二阶方法需要 Hessian，见
    [二阶方法与拟牛顿](https://github.com/junxnone/math/issues/82)

## 常见误区

  - 布局约定不同，同一个公式可能差一个转置；推导全程要用同一种约定
  - 矩阵乘法不可交换，求导时不能把因子随意换位；只有在迹里可以循环移动
  - 对矩阵求导的结果与该矩阵同形（分母布局），形状不对说明推导出错，可以用形状检查
