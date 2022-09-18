---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# 行列

## 行列の掛け算

$$
A = \begin{pmatrix}
a & b \\
c & d \\
\end{pmatrix}\\
B = \begin{pmatrix}
e\\
f\\
\end{pmatrix}
\\
A \cdot B = \begin{pmatrix}
a*e + b*f\\
c*e+d*f\\
\end{pmatrix}
$$

```python
x = np.array([1,2])
w = np.array([[4,8],[6,3]])
x.dot(w)
# array([16,14])
```

```{note}
- 計算できる条件：Aの列数=Bの行数
- 結果.shape=(前の行数, 後ろの列数)
```

## 行列式
$$
A =
\begin{pmatrix}
a&b\\
c&d
\end{pmatrix}の時、Aの行列式を\\
\det A、 |A|、
\begin{vmatrix}
a&b\\
c&d
\end{vmatrix}と表し、\\
|A|=a*d-b*c
$$

### 求め方
#### 2x2行列
$$
\begin{vmatrix}
a&b\\
c&d
\end{vmatrix}
=a*d-b*c
$$

#### 3x3行列(サラスの公式)
$$
\begin{vmatrix}
a_{11} & a_{12} & a_{13}\\
a_{21} & a_{22} & a_{23}\\
a_{31} & a_{32} & a_{33}
\end{vmatrix}\\
=a_{11} a_{22} a_{33}+a_{12} a_{23}a_{31}+a_{13}a_{32}a_{21}\\
-a_{13}a_{22} a_{31}
-a_{12}a_{21}a_{33}
-a_{11}a_{32} a_{23}
$$

```python
np.linalg.det(A)
```

### 交換性
行列の2列を入れ替えた場合、または2行を入れ替えた場合、行列式は元の行列式の-1倍になる。

$$
\begin{vmatrix}
a_{11} & a_{12} & a_{13}\\
a_{21} & a_{22} & a_{23}\\
a_{31} & a_{32} & a_{33}
\end{vmatrix}
=
-
\begin{vmatrix}
a_{21} & a_{22} & a_{23}\\
a_{11} & a_{12} & a_{13}\\
a_{31} & a_{32} & a_{33}
\end{vmatrix}
$$

## 逆行列

元の行列とかけると単位行列になる行列、すなわち
$A^{-1} \cdot A = I$を満たす$A^{-1}$を$A$の逆行列という。

ただし、行列式$|A|=0$の時は$A$は逆行列を持たない。

### 求め方
#### 2x2行列の逆行列
2x2の行列$A=\begin{pmatrix}a&b\\c&d\end{pmatrix}$の逆行列は
$$
A^{-1} = \frac{1}{ad-bc}
\begin{pmatrix}
d&-b\\
-c&a
\end{pmatrix}
$$

#### 掃き出し法

#### numpy
```python
import numpy as np
import numpy.linalg as LA

A = np.array([[3,5],[2,-2]])
LA.inv(A)
#=>array([[ 0.125 ,  0.3125],
#       [ 0.125 , -0.1875]])
```

## 対象行列
転置しても元の行列とおなじになる行列のこと

$$ 
A = A^T\\
$$

対象行列の例

$$
\begin{pmatrix}
1 & 2\\
2 & 3
\end{pmatrix}\\
単位行列
\begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
\end{pmatrix}\\
$$

## 直行行列

転置すると元の行列の逆行列になる行列を、直行行列と言う。

$$
R^T = R^{-1}\\
RR^T = I
$$

## 対角行列

対角成分以外が０な行列

$$
\begin{pmatrix}
8 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 3 & 0\\
0 & 0 & 0 & 9\\
\end{pmatrix}
$$


## 固有値・固有値ベクトル
あるn次正方行列$A$に対し、

$$Ax = \lambda x$$

を満たすn次元ベクトル$x (x \neq 0)$が存在する時、

$$
\lambda : Aの固有値\\
x : \lambdaに対する固有ベクトル
$$
と言う

### 求め方
#### 固有値
$$
Ax = \lambda xを満たすx,\lambdaを求める\\
単位ベクトルEを使い変形すると\\
(A-\lambda E)=0\\
すなわち\\
|A-\lambda E|=0\\
を考える
$$
#### 固有ベクトル
$$
\lambda = \lambda_1, \lambda_2, \dots を代入して、\\
(A-\lambda_i E)x=0\\
を満たすx_iを求める。
$$

例：

$$
\begin{pmatrix}3&2&0\\0&2&0\\0&0&1\end{pmatrix}の固有値、固有ベクトルは？
$$

$$
\begin{pmatrix}3-\lambda & 2 & 0\\
0 & 2 - \lambda & 0\\
0 & 0 & 1-\lambda
\end{pmatrix}=0
$$

$$
(3-\lambda)(2-\lambda)(1-\lambda)=0\\
\therefore \lambda=3,2,1
$$

固有ベクトルは、

1. $\lambda=1$の時

$$
(A-\lambda_1 E)x=0\\
\begin{pmatrix}
3-1 & 2 & 0\\
0 & 2-1 & 0\\
0 & 0 & 1-1
\end{pmatrix}
\begin{pmatrix}
x_1\\
x_2\\
x_3
\end{pmatrix}
=0\\

\begin{cases}
2x_1+2x_2=0	\therefore x_1=-x_2\\
x_2=0	\therefore x_2=0\\
0=0\\
\end{cases}\\
\therefore \lambda=1の時、固有値は
\begin{pmatrix}
0\\0\\1
\end{pmatrix}
の定数倍
$$

2. $\lambda=2$の時

$$
(A- 2 E)x=0\\
\begin{pmatrix}
3-2 & 2 & 0\\
0 & 2-2 & 0\\
0 & 0 & 1-2
\end{pmatrix}
\begin{pmatrix}
x_1\\
x_2\\
x_3
\end{pmatrix}
=0\\

\begin{cases}
x_1+2x_2=0	\therefore x_1=-2x_2\\
0=0\\
-x_3=0 	\therefore x_3=0\\
\end{cases}\\
任意の定数Sを用いると\\

\begin{pmatrix}
x_1\\
x_2\\
x_3\\
\end{pmatrix}
=
\begin{pmatrix}
-2S\\
S\\
0\\
\end{pmatrix}
=S
\begin{pmatrix}
-2\\
1\\
0\\
\end{pmatrix}
\\

\therefore \lambda=2の時、固有値は
\begin{pmatrix}
-2\\1\\0
\end{pmatrix}
の定数倍
$$

3. $\lambda=3$の時

$$
(A- 3E)x=0\\
\begin{pmatrix}
3-3 & 2 & 0\\
0 & 2-3 & 0\\
0 & 0 & 1-3
\end{pmatrix}
\begin{pmatrix}
x_1\\
x_2\\
x_3
\end{pmatrix}
=0\\

\begin{cases}
2x_2=0	\therefore x_2=0\\
-x_2=0\\
-2x_3=0 	\therefore x_3=0\\
\end{cases}\\

\therefore \lambda=3の時、固有値は
\begin{pmatrix}
1\\0\\0
\end{pmatrix}
の定数倍
$$

### numpy
```python
import numpy as np
import numpy.linalg as LA

A = np.array([
	[3, 2, 0],
	[0, 2, 0],
	[0, 0, 1]
])
w, v = LA.eig(A)
# 固有値
print(w)
#array([3., 2., 1.])
# 固有ベクトル; 縦に見る
print(v)
#array([[ 1.        , -0.89442719,  0.        ],
#       [ 0.        ,  0.4472136 ,  0.        ],
#       [ 0.        ,  0.        ,  1.        ]])
```

## 固有値分解

正方行列$A$を、
- 固有値を対角線上に並べた固有値行列$\Lambda$と
- 固有ベクトルを並べた行列$V$
を使ってこのように表すこと

$$A=V \Lambda V^{-1}$$

### 求め方
#### numpy

```python
import numpy as np
import numpy.linalg as LA

A = np.array([
	[3, 2, 0],
	[0, 2, 0],
	[0, 0, 1]
])
w, v = LA.eig(A)

# 固有値
print(w)
#array([3., 2., 1.])

# 固有値ベクトル
Q = np.diag(w)
print(Q)
#array([[3., 0., 0.],
#       [0., 2., 0.],
#       [0., 0., 1.]])

# 固有ベクトル
print(v)
#array([[ 1.        , -0.89442719,  0.        ],
#       [ 0.        ,  0.4472136 ,  0.        ],
#       [ 0.        ,  0.        ,  1.        ]])

# 固有ベクトル（右）
R = LA.inv(v) # 逆行列を得る
print(R)
#array([[1.        , 2.        , 0.        ],
#       [0.        , 2.23606798, 0.        ],
#       [0.        , 0.        , 1.        ]])
```
numpyで得らた結果を使ってAを固有値分解すると、

$$
A=vQR=
\begin{pmatrix}
1 & -2 & 0\\
0 & 1 & 0\\
0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
3 & 0 & 0\\
0 & 2 & 0\\
0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
1 & 2 & 0\\
0 & \sqrt{5} & 0\\
0 & 0 & 1
\end{pmatrix}
$$


## 対角化

正方行列$A$を、$A$の固有ベクトルを列に並べた行列$P$とその逆行列$P^{-1}$で挟み、固有値がならんだ対角行列$D$に線形変換する事。

### 対角化のメリット
- 計算が楽になる

### 対角化可能

次数と同じ数の固有ベクトルが互いに一次独立

### 例

$
A = \begin{pmatrix}
1 & 2 & 0\\
0 & 3 & 0\\
2 & -4 & 2
\end{pmatrix}
$
を対角化せよ。

```{code-cell} python
import numpy as np
import numpy.linalg as LA
A = np.array([
	[1,2,0],
	[0,3,0],
	[2,-4,2]
	])
w,P =LA.eig(A)
# Aの固有値
w
```

```{code-cell} python
# 固有ベクトルを列ベクトルとして並べた行列P
P
```

```{code-cell} python
# Pの逆行列
P1 = LA.inv(P)
```

$X=\begin{pmatrix}3&1\\2&2\end{pmatrix}$のn乗は？

```{code-cell} python
import numpy as np
import numpy.linalg as LA
A = np.array([
	[3,1],
	[2,2]
	])
w,v=LA.eig(A)
w
```

Aを対角化した物がD

```{code-cell} python
D=np.diag(w)
D
```

```{code-cell} python
v
```

vの整数倍であれば問題ない。計算しやすいように、縦の要素毎にきりの良い数字に変換する

$$
V=\begin{pmatrix}
1 & 1\\
1 & -2
\end{pmatrix}
$$

```{code-cell} python
# 整数化したv
V = np.array([[
	[1, 1],
	[1, -2]
]])

# 逆行列を求めるコマンド
V1 = LA.inv(V)
V1
```

$V^{-1}$の変換は行列全体に対して係数を掛ける方法っぽい

$$
V^{-1}=
\dfrac{1}{3}
\begin{pmatrix}
2 & 1\\
1 & -1
\end{pmatrix}
$$

```{code-cell} python
# 検算
V1 = np.array([
	[2, 1],
	[1, -1]
])

1/3 * V @ D @ V1
```

$$
A=V \Lambda V^{-1}\\
=
\frac{1}{3}
\begin{pmatrix}
1&1\\
1&-2
\end{pmatrix}
\begin{pmatrix}
4&0\\
0&1
\end{pmatrix}
\begin{pmatrix}
2&1\\
1&-1
\end{pmatrix}
\\
A^n =V \Lambda^n V^{-1}\\
=
\frac{1}{3}
\begin{pmatrix}
1&1\\
1&-2
\end{pmatrix}
\begin{pmatrix}
4&0\\
0&1
\end{pmatrix}^n
\begin{pmatrix}
2&1\\
1&-1
\end{pmatrix}\\
=
\frac{1}{3}
\begin{pmatrix}
1&1\\
1&-2
\end{pmatrix}
\begin{pmatrix}
4^n&0\\
0&1^n
\end{pmatrix}
\begin{pmatrix}
2&1\\
1&-1
\end{pmatrix}\\
=\frac{1}{3}
\begin{pmatrix}
4^n	 & 1\\
4^n & -2
\end{pmatrix}
\begin{pmatrix}
2&1\\
1&-1
\end{pmatrix}\\
=\frac{1}{3}
\begin{pmatrix}
2*4^n+1 & 4^n-1\\
2*4^n-2 & 4^n+2
\end{pmatrix}

$$


## 特異値分解

Singular Value Decomposition SVD
: 次元削減のために用いられる手法
= 長方形行列の固有値分解

### 手順
任意の行列$A$を$A=USV^T$に特異値分解してみる

$$
A = \begin{pmatrix}
1&2&3\\
3&2&1
\end{pmatrix}
$$


```{code-cell} python
# linalgモジュールはLAとしてimportする
import numpy as np
import numpy.linalg as LA

# 行列Aを定義する
a = np.array([
              [1,2,3],
              [3,2,1]
])

# AA^Tを求める
AAT = np.dot(a, a.T)
AAT
```

```{code-cell} python
# 特異値分解のコマンド
U, S, Vt = LA.svd(a, full_matrices=True)
# 左特異値行列
U
```

```{code-cell} python
# 特異値
S
```

```{code-cell} python
# 対角行列にする
S = np.diag(S)
S
```

```{code-cell} python
# 左特異値行列の転地
Vt
```

```{code-cell} python
# shapeをそろえる
S2 = np.pad(S, ((0, 0), (0, 1)))
S2
```

```{code-cell} python
# 検算
U @ S2 @ Vt
```

よって、

$$ U =  \begin{pmatrix}
- \dfrac{1}{\sqrt{2}} &
- \dfrac{1}{\sqrt{2}}\\
- \dfrac{1}{\sqrt{2}} &
\dfrac{1}{\sqrt{2}}
\end{pmatrix}
$$

$$
S=\begin{pmatrix}
2\sqrt{6} & 0 &0\\
0 & 2 & 0
\end{pmatrix}
$$

$$ V^T =  \begin{pmatrix}
\dfrac{1}{\sqrt{3}} &
\dfrac{1}{\sqrt{3}} &
\dfrac{1}{\sqrt{3}} \\
- \dfrac{1}{\sqrt{2}} &
0 &
\dfrac{1}{\sqrt{2}}\\
\dfrac{1}{\sqrt{6}} &
-\dfrac{2}{\sqrt{6}} &
\dfrac{1}{\sqrt{6}} &
\end{pmatrix}
$$


