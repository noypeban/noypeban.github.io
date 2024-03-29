# 確率分布

## 離散型確率変数

Xが取りうる値が飛び飛びの値しか取らない確率変数
- コインの表が出る確率
- サイコロのそれぞれの目が出る確率

## 確率密度関数

連続型確率変数の分布を表す関数。$X$が$a$以上$b$以下となる確率を$P(a \leq X \leq b)$とすると、確率密度関数$f(x)$は、

$$
f(x) \geq 0\\

P(a \leq X \leq b) = \int _a^b f(x) dx
$$

また、$X$が取りうる値の下限を$A$, 上限を$B$とすると、$f(x)$が確率密度関数であれば積分すると１になる。

$$ \int _A^B f(x) dx = 1 $$


## 期待値

> 確率変数の期待値は、確率変数がとる値とその値をとる確率の積を全て足し合わせたもので、確率変数の平均値を表します
> -- [統計web](https://bellcurve.jp/statistics/course/6712.html)

離散的な確率分布$P(x)$における、ある確率変数$f(x)$の期待値

$$
E(f) = \sum f(x)P(x)
$$

連続関数の期待値

$$
E(f) = \int ^{\infty}_{-\infty} x f(x) dx
$$

### 例題

#### サイコロの出る目の期待値

サイコロの出る目(X)|1|2|3|4|5|6
-|-|-|-|-|-|-
確率(P(X))|$\dfrac{1}{6}$|$\dfrac{1}{6}$|$\dfrac{1}{6}$|$\dfrac{1}{6}$|$\dfrac{1}{6}$|$\dfrac{1}{6}$

$$
E(X) = \sum^6_{i=1} x_i pi\\
= 1 \times \dfrac{1}{6} + 2 \times \dfrac{1}{6} + 3 \times \dfrac{1}{6} + 4 \times \dfrac{1}{6} + 5 \times \dfrac{1}{6} + 6 \times \dfrac{1}{6}\\
= \dfrac{7}{2} = 3.5
$$

## 分散

確率における分散は、
> 「確率変数の取りえる値と期待値（平均値）の差の2乗」と「確率」との積を全て足し合わせたもの
> -- [統計web](https://bellcurve.jp/statistics/course/6716.html)

$V(X) = \sum_{i=1}^n (x_i - E(X))^2 p_i$

または、期待値のみを使って

$$
V(X) = E(X^2)-{E(X)}^2\\
あるいは\\
V(X) = E{((X-E(X))^2)}
$$

### 例題

#### サイコロの出る目の分散

$$
V(X) = \sum^n_{i=1} (x_i-E)^2p_i\\
=\sum^n_{i=1} (x_i - 3.5)^2 p_i\\
=\dfrac{(1-3.5)^2}{6} +
\dfrac{(2-3.5)^2}{6} +
\dfrac{(3-3.5)^2}{6} +
\dfrac{(4-3.5)^2}{6} +
\dfrac{(5-3.5)^2}{6} +
\dfrac{(6-3.5)^2}{6}\\
=\dfrac{1}{6}(6.25+2.25+0.25+0.25+2.25+6.25)\\
=\dfrac{17.5}{6}=\dfrac{35}{12}
$$

## ベルヌーイ分布

確率変数
: １回だけのベルヌーイ試行（成功[X=x]のときp=1，失敗のときp=0）

確率関数
: $P(X=x)=p^x(1-p)^{1-p}$

期待値
: $E[X] = p$

分散
: $V[X]=p(1-p)$

## 2項分布

確率変数
: 複数回のベルヌーイ試行

確率関数
: $P(X=x|n,p)={}_nC_k p^k (1-p)^{n-k}$ 試行回数=n, 成功確率=p

期待値
: $E[X]=np$

分散
: $V[X]=np(1-p)$

## 正規分布

確率変数
:平均$\mu$、分散$\sigma^2$の正規分布

確率関数
: $f(X)=\dfrac{1}{\sqrt{2 \pi \sigma ^2}}
exp
[-\dfrac{(x-\mu)^2}{2\sigma ^2}
]$

期待値
: $E(X)=\mu$

分散
: $SD(X)=\sigma$

## 標準正規分布

確率変数
: 平均０、分散１の正規分布を標準正規分布と言う

確率関数
: $f(x)=\dfrac{1}{\sqrt{2\pi}}
exp[
-\dfrac{x^2}{x}]$

期待値
: $E(X)=1$

分散
: $V(X)=1$