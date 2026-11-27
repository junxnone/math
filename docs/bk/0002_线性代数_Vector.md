-----

| Title     | 线性代数 Vector                                       |
| --------- | ------------------------------------------------- |
| Created @ | `2022-02-22T09:24:37Z`                            |
| Updated @ | `2026-11-27T01:32:58Z`                            |
| Labels    | \`\`                                              |
| Edit @    | [here](https://github.com/junxnone/math/issues/2) |

-----

# 向量

向量是既有**大小**又有**方向**的量，在代数上是一组有序的数。线性代数、机器学习中的样本、参数、嵌入，都用向量表示。

## 定义与表示

$$
a=\\begin{bmatrix}a\_1\\a\_2\\vdots\\a\_n\\end{bmatrix}\\in\\mathbb{R}^{n},\\qquad
\\lVert a\\rVert=\\sqrt{a\_1^2+a\_2^2+\\cdots+a\_n^2} $$

其中：

  - $a$：$n$ 维列向量；$a\_i$：第 $i$ 个分量；$\\mathbb{R}^n$：$n$ 维实向量空间
  - $\\lVert a\\rVert$：向量的模（长度），即欧氏范数，详见
    [范数](https://github.com/junxnone/math/issues/11)
  - 模为 1 的向量称为单位向量；任意非零向量除以自身的模得到同方向的单位向量 $\\hat a=a/\\lVert a\\rVert$

基本运算：

  - 加法：$a+b=(a\_1+b\_1,\\dots,a\_n+b\_n)$，几何上是平行四边形法则
  - 数乘：$ka=(ka\_1,\\dots,ka\_n)$，$k\>0$ 时方向不变，$k\<0$ 时反向，长度乘以 $\\lvert
    k\\rvert$

## 向量点乘

  - 点乘 - Dot Product/Scalar Product
  - $a \\cdot b = \\sum\_{i=1}^{n} a\_{i}b\_{i}$ - $a = \[a\_{1},
    a\_{2}, ..., a\_{n}\]$ - $b = \[b\_{1}, b\_{2}, ..., b\_{n}\]$
  - $a \\cdot b = |a||b|cos\\theta $
  - $a \\cdot b = b \\cdot a $
  - $a \\cdot (b + c) = a \\cdot b + a \\cdot c$

其中：

  - $a\\cdot b$：点乘，结果是一个**标量**；也可以写成 $a^\\top b$
  - $\\theta$：两个向量之间的夹角，$0\\le\\theta\\le\\pi$
  - 前两个式子分别是「代数定义」和「几何定义」，二者等价

### 几何意义

  - $a\\cdot b\>0$：夹角为锐角（方向大致相同）；$=0$：垂直（正交）；$\<0$：夹角为钝角
  - $b$ 在 $a$ 方向上的投影长度：$\\mathrm{proj}\_a b=\\dfrac{a\\cdot b}{\\lVert
    a\\rVert}$；投影向量：$\\dfrac{a\\cdot b}{a\\cdot a},a$
  - 夹角余弦（余弦相似度）：$\\cos\\theta=\\dfrac{a\\cdot b}{\\lVert
    a\\rVert,\\lVert b\\rVert}$
  - Cauchy–Schwarz 不等式：$\\lvert a\\cdot b\\rvert\\le\\lVert
    a\\rVert\\lVert b\\rVert$，等号当且仅当 $a,b$ 共线

## 向量叉乘

  - 叉乘 - Cross Product/Vector Product

叉乘只对三维向量定义，结果是**一个向量**，垂直于 $a$ 和 $b$ 所在的平面：

$$ a\\times
b=\\begin{vmatrix}\\mathbf{i}&\\mathbf{j}&\\mathbf{k}\\a\_1\&a\_2\&a\_3\\b\_1\&b\_2\&b\_3\\end{vmatrix}=\\begin{bmatrix}a\_2b\_3-a\_3b\_2\\a\_3b\_1-a\_1b\_3\\a\_1b\_2-a\_2b\_1\\end{bmatrix},\\qquad
\\lVert a\\times b\\rVert=\\lVert a\\rVert\\lVert b\\rVert\\sin\\theta
$$

其中：

  - $\\mathbf{i},\\mathbf{j},\\mathbf{k}$：三个坐标轴方向的单位向量；行列式按第一行展开即得右侧的分量
  - $\\lVert a\\times b\\rVert$：以 $a,b$ 为邻边的平行四边形的面积
  - 方向由**右手定则**确定：四指从 $a$ 转向 $b$，拇指所指方向即 $a\\times b$

性质：

  - 反交换：$a\\times b=-(b\\times a)$；因此 $a\\times a=0$
  - $a\\times b=0\\iff a,b$ 共线（平行）
  - 分配律：$a\\times(b+c)=a\\times b+a\\times c$；不满足结合律

### 标量三重积

$$ a\\cdot(b\\times c)=\\det\\begin{bmatrix}a\&b\&c\\end{bmatrix} $$

其中：右边是以 $a,b,c$ 为列的 $3\\times3$ 行列式；绝对值等于以三个向量为棱的平行六面体体积，为 0 时三向量共面。

## 点乘与叉乘对比

| 对比项   | 点乘 $a\\cdot b$ | 叉乘 $a\\times b$    |
| ----- | -------------- | ------------------ |
| 结果    | 标量             | 向量（三维）             |
| 几何意义  | 一个向量在另一个上的投影   | 垂直于两者的向量，模为平行四边形面积 |
| 交换性   | 可交换            | 反交换                |
| 为零的条件 | 垂直             | 平行                 |
| 适用维度  | 任意维            | 三维（七维有特例）          |

表中：对比结论：点乘衡量「像不像」（同向程度），叉乘衡量「偏不偏」（垂直方向与面积）。

## 在机器学习中的作用

  - 相似度：嵌入向量之间的点乘或余弦相似度，是检索、注意力 $QK^\\top$ 的基础
  - 线性模型：预测 $w^\\top x+b$ 就是权重向量与特征向量的点乘
  - 正交与独立：两个向量正交意味着互不包含对方的方向信息，见
    [线性相关无关](https://github.com/junxnone/math/issues/24)、[投影](https://github.com/junxnone/math/issues/42)

## 相关文章

  - [范数](https://github.com/junxnone/math/issues/11)、[矩阵](https://github.com/junxnone/math/issues/4)、[向量空间](https://github.com/junxnone/math/issues/34)、[线性相关无关](https://github.com/junxnone/math/issues/24)
