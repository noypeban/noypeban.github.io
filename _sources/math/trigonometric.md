# 三角関数
## 定義

単位円上の点$P(x,y)$と$x$軸の作る角$\theta$を使うと、三角関数は以下のように表せられる。

$$
\sin \theta = y\\
\cos \theta = x\\
\tan \theta = \dfrac{y}{x} = \dfrac{\sin \theta}{\cos \theta}
$$

## 公式

$$
\sin^2 \theta + \cos^2 \theta = 1\\
\tan^2 \theta + 1 = \dfrac{1}{\cos^2 \theta}\\
$$ 

導出は、
- 円の方程式$x^2+y^2=1$に$x=\cos \theta$, $y=\sin \theta$を代入
- $\sin^2 \theta+\cos^2 \theta=1$を$\cos^2 \theta$を割る

::::{grid} 2
:::{grid-item}
$$
\sin(90^{\circ}-\theta)=\cos \theta\\
\sin(90^{\circ}+\theta)=\cos \theta\\
\sin(180^{\circ}+\theta)=-\sin \theta
$$
:::
:::{grid-item}
$$
\cos(90^{\circ}-\theta)=\sin \theta\\
\cos(90^{\circ}+\theta)=-\sin \theta\\
\cos(90^{\circ}+\theta)=-\cos \theta
$$
:::
::::

## 正弦定理

$\triangle ABC$において$AB=c, BC=a, CA=b$とする。  
$\angle ABC=B, \angle BCA=C, \angle CAB=a$とする。  
$\triangle ABC$の外接円の半径を$R$とする。

$$
\dfrac{a}{\sin A} = 
\dfrac{b}{\sin B} = 
\dfrac{c}{\sin C} = 2R
$$

### 例題：ほかの角を求める

> a = 4, A = 30º, B = 105º のとき、c の値を求めよ。  
> -- [スタディクラブ](https://study-club.jp/news/seigen-yogen/)

$$
\angle C = 180^{\circ} - (30+105) = 45^{\circ}\\
$$

正弦定理より、

$$
\dfrac{a}{\sin A} = 
\dfrac{c}{\sin C}\\
=
\dfrac{4}{\sin 30^{\circ}} = 
\dfrac{c}{\sin 45^{\circ}}\\
\therefore
c = \dfrac{4}{\sin 30^{\circ}}\times \sin 45^{\circ}\\
= \dfrac{4\cdot 2}{\sqrt{2}}\\
= 4 \sqrt{2}

