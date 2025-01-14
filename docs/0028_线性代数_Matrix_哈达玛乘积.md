---
Title | 线性代数 Matrix 哈达玛乘积
-- | --
Created @ | `2025-01-14T07:04:52Z`
Updated @| `2025-01-14T07:04:52Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/28)

---
# 哈达玛乘积

 - **Hadamard Product**/**Element-Wise Product**

## 性质
- **交换律:** $A \circ B = B \circ A$ 
- **结合律:** $A \circ (B \circ C) = (A \circ B) \circ C$
- **分配律:** $A \circ (B + C) = A \circ B + A \circ C$

> $\circ$ 与 $\odot$ 都可以表示点积

## 例子

$$\left[ \begin{array}{ccc}    
 a_{11} & a_{12} & a_{13}\\ 
 a_{21} & a_{22} & a_{23}\\
 a_{31} & a_{32} & a_{33} 
\end{array} \right] \circ 
\left[ \begin{array}{ccc} 
    b_{11} & b_{12} & b_{13}\\
    b_{21} & b_{22} & b_{23}\\
    b_{31} & b_{32} & b_{33} \end{array} \right] = 
\left[ \begin{array}{ccc}
     a_{11}\times b_{11} & a_{12}\times b_{12} & a_{13}\times b_{13}\\
     a_{21}\times b_{21} & a_{22}\times b_{22} & a_{23}\times b_{23}\\
     a_{31}\times b_{31} & a_{32}\times b_{32} & a_{33}\times b_{33}
 \end{array} \right]$$
