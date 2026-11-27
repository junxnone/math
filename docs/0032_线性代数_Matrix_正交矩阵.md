---
Title | 线性代数 Matrix 正交矩阵
-- | --
Created @ | `2025-01-14T08:36:28Z`
Updated @| `2026-11-27T01:33:13Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/32)

---
# 正交矩阵

- 若一个 $n$ 阶方阵 $A$ 满足 $A^{T}A = AA^{T}=I$ （ $I$ 是 $n$ 阶单位矩阵），则称 $A$ 为正交矩阵。
- 正交矩阵的转置矩阵就是它的逆矩阵，即 $A^{T}=A^{-1}$

$$A=\begin{bmatrix} a_1 & a_2 & ... & a_n \\ \end{bmatrix}$$

$$A^T=\begin{bmatrix} a_1^T \\ a_2^T \\ ... \\ a_n^T \\ \end{bmatrix} $$

$$A^TA = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
\end{bmatrix}$$ 


## 性质
- 正交矩阵的行列式的值为 $\pm1$ 
- 若 $A$ 和 $B$ 是正交矩阵，那么 $AB$ 也是正交矩阵。

## 几何意义
- 在二维空间中，正交矩阵代表旋转和反射变换。
  - 以旋转矩阵为例:

$$\begin{pmatrix}\cos\theta&-\sin\theta\\
\sin\theta&\cos\theta\end{pmatrix}$$

表示将向量逆时针旋转 $\theta$ 角度的变换。

- 在三维空间中，正交矩阵同样可以表示旋转和反射等刚体变换。
  - 例如，绕 $z$ 轴旋转 $\alpha$ 角度的旋转矩阵为:
 
$$R_{z}=\begin{pmatrix}\cos\alpha&-\sin\alpha&0\\
\sin\alpha&\cos\alpha&0\\
0&0&1\end{pmatrix}$$


## 定义的含义

- $A^TA=I$ 说明 $A$ 的**列向量是一组标准正交基**：每列长度为 1，不同列之间点乘为 0；$AA^T=I$ 则说明**行向量**也是标准正交基
- $I$：$n$ 阶单位矩阵；正交矩阵一定可逆，且逆就是转置，所以求逆几乎没有计算代价

## 更多性质

- **保长度、保夹角：** $\lVert Qx\rVert=\lVert x\rVert$，$(Qx)\cdot(Qy)=x\cdot y$。推导：$\lVert Qx\rVert^2=x^TQ^TQx=x^Tx$
- **特征值模为 1：** 所有特征值满足 $\lvert\lambda\rvert=1$（实数时为 $\pm1$，复数时在单位圆上）
- **行列式为 $\pm1$：** $\det Q=1$ 的是**旋转**，$\det Q=-1$ 的包含**反射**
- **条件数为 1：** 乘以正交矩阵不放大误差，数值上最稳定，见 [范数与条件数](/0045_线性代数_Matrix_范数与条件数)

$$
O(n)=\{Q\in\mathbb{R}^{n\times n}\mid Q^{T}Q=I\},\qquad SO(n)=\{Q\in O(n)\mid\det Q=1\}
$$

其中：$O(n)$ 称为正交群（含旋转与反射），$SO(n)$ 称为特殊正交群（只含旋转）；三维空间的刚体旋转就是 $SO(3)$，机器人学中用它表示姿态（见 aiwiki 的 [RL Robot Rotation](https://github.com/junxnone/aiwiki/issues/777)）。

## 反射矩阵：Householder 变换

给定非零向量 $v$，关于过原点、法向为 $v$ 的超平面的镜面反射为：

$$
H=I-\frac{2\,vv^{T}}{v^{T}v}
$$

其中：$H$ 是对称且正交的矩阵（$H=H^T=H^{-1}$），$\det H=-1$；$Hx$ 把 $x$ 沿 $v$ 方向的分量反向。选取合适的 $v$ 可以把任意向量变换成只剩第一个分量非零，是 QR 分解的基本工具。

## 与矩阵分解的联系

- **QR 分解：** $A=QR$，$Q$ 为正交矩阵，$R$ 为上三角矩阵；施密特正交化、Householder 反射和 Givens 旋转都可以得到它，见 [矩阵分解](/0040_线性代数_Matrix_矩阵分解)
- **SVD：** $A=U\Sigma V^{T}$，其中 $U,V$ 是正交矩阵，见 [SVD](/0012_线性代数_SVD)
- **谱定理：** 实对称矩阵可由正交矩阵对角化 $A=Q\Lambda Q^{T}$，见 [特征值与特征向量](/0036_线性代数_特征值与特征向量)


## 求正交矩阵的方法

### 施密特正交化方法
- 施密特正交化方法：如果已知一组线性无关的向量组 $\left\{\vec{v}_{1},\vec{v}_{2},\cdots,\vec{v}_{n}\right\}$ ，可以通过施密特正交化过程得到一组正交向量组 $\left\{\vec{u}_{1},\vec{u}_{2},\cdots,\vec{u}_{n}\right\}$ ，然后将这些正交向量组单位化，得到标准正交向量组 $\left\{\hat{e}_{1},\hat{e}_{2},\cdots,\hat{e}_{n}\right\}$ 。以这些标准正交向量组为列向量组成的矩阵就是正交矩阵。

## 在机器学习中的作用

- 正交初始化与正交约束：保持梯度范数，缓解深层网络和 RNN 的梯度消失 / 爆炸
- 旋转位置编码、坐标变换、PCA 的投影基，都是正交变换
- 数据白化与去相关：用正交变换把协方差矩阵对角化

## 常见误区

- 正交矩阵要求**列向量标准正交**，只有「列互相垂直」但长度不为 1 的矩阵不是正交矩阵
- 正交矩阵必须是方阵；$m\times n$（$m>n$）且 $A^TA=I$ 的矩阵称为列正交矩阵，但 $AA^T\ne I$
- 行列式为 $\pm1$ 是必要条件，不是充分条件


