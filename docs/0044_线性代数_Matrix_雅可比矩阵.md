---
Title | 线性代数 Matrix 雅可比矩阵
-- | --
Created @ | `2026-11-24T14:42:25Z`
Updated @| `2026-11-25T09:33:39Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/44)

---
# 雅可比矩阵

雅可比矩阵（Jacobian）是多元向量函数的“导数”：它给出函数在某点附近最好的线性近似。这样非线性问题就可以用线性代数处理——Newton 法、Gauss-Newton、反向传播、变量替换都依赖它。

## 定义

对 $\mathbf{f}:\mathbb{R}^n\to\mathbb{R}^m$，$\mathbf{f}(\mathbf{x})=(f_1,\dots,f_m)^\top$：

$$
J=\frac{\partial\mathbf{f}}{\partial\mathbf{x}}=\begin{bmatrix}
\dfrac{\partial f_1}{\partial x_1}&\cdots&\dfrac{\partial f_1}{\partial x_n}\\
\vdots&\ddots&\vdots\\
\dfrac{\partial f_m}{\partial x_1}&\cdots&\dfrac{\partial f_m}{\partial x_n}
\end{bmatrix}\in\mathbb{R}^{m\times n}
$$

其中：

- $\mathbf{x}=(x_1,\dots,x_n)^\top$：输入；$f_i$：第 $i$ 个输出分量
- $J_{ij}=\partial f_i/\partial x_j$：第 $j$ 个输入对第 $i$ 个输出的瞬时影响，$J$ 在每个点处取值
- 标量函数（$m=1$）时 $J$ 是梯度的转置；梯度的雅可比就是 Hessian 矩阵

## 局部线性化

$$
\mathbf{f}(\mathbf{x}+\boldsymbol\delta)\approx\mathbf{f}(\mathbf{x})+J(\mathbf{x})\,\boldsymbol\delta
$$

其中：

- $\boldsymbol\delta$：输入的微小扰动
- $J(\mathbf{x})\boldsymbol\delta$：输出的一阶变化；因此在 $\mathbf{x}$ 附近，非线性函数表现得像线性变换 $J$（见 [线性变换](/0039_线性代数_线性变换)）
- 近似的精度随 $\|\boldsymbol\delta\|$ 减小而提高

## 雅可比行列式与变量替换

当 $m=n$ 时 $\det J$ 称雅可比行列式，是局部体积的缩放因子：

$$
\iint g(x,y)\,dx\,dy=\iint g\bigl(x(u,v),y(u,v)\bigr)\,\left|\det J\right|\,du\,dv
$$

其中 $J=\partial(x,y)/\partial(u,v)$，$|\det J|$ 是面积元的缩放倍数。例：极坐标 $x=r\cos\theta,\ y=r\sin\theta$：

$$
J=\begin{bmatrix}\cos\theta&-r\sin\theta\\\sin\theta&r\cos\theta\end{bmatrix},\qquad \det J=r
$$

所以 $dx\,dy=r\,dr\,d\theta$。$\det J\ne0$ 时函数局部可逆（反函数定理），$J^{-1}$ 就是反函数的雅可比。

## 链式法则

$$
J_{\mathbf{g}\circ\mathbf{f}}(\mathbf{x})=J_{\mathbf{g}}\bigl(\mathbf{f}(\mathbf{x})\bigr)\,J_{\mathbf{f}}(\mathbf{x})
$$

其中：

- $\mathbf{f}:\mathbb{R}^n\to\mathbb{R}^k$，$\mathbf{g}:\mathbb{R}^k\to\mathbb{R}^m$；复合的雅可比等于两者雅可比的矩阵乘积
- 神经网络的反向传播就是沿计算图把各层雅可比连乘（实际中计算雅可比与向量的乘积而非显式矩阵）

## 应用

- 非线性方程组 $\mathbf{f}(\mathbf{x})=\mathbf{0}$ 的 Newton 法：$\mathbf{x}_{k+1}=\mathbf{x}_k-J^{-1}\mathbf{f}(\mathbf{x}_k)$
- 非线性最小二乘（Gauss-Newton）：残差 $\mathbf{r}(\mathbf{x})$ 的雅可比 $J$ 给出更新量 $\boldsymbol\delta=-(J^\top J)^{-1}J^\top\mathbf{r}$，即解线性最小二乘（见 [投影](/0042_线性代数_投影)）；SLAM、Bundle Adjustment 都基于此
- 机器人：关节速度与末端速度之间 $\dot{\mathbf{p}}=J\dot{\mathbf{q}}$；奇异位形即 $J$ 降秩（见 [秩](/0029_线性代数_Matrix_秩)）
- 分析数值稳定性：$J$ 的条件数衡量输入误差的放大（见 [范数与条件数](/0045_线性代数_Matrix_范数与条件数)）

## Reference

- [Jacobian matrix and determinant - Wikipedia](https://en.wikipedia.org/wiki/Jacobian_matrix_and_determinant)
- [导数](/0009_Math_Derivative)


