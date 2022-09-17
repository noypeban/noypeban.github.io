# 最適化アルゴリズム

## 最尤推定(MLE)

簡単に言うと
: サンプルデータが得られる確率が最大になる物を探す
概要
: パラメータ$\theta$に従う分布の密度関数を$f(x; \theta)$とする。尤度関数を$L(\theta; x)=f(x; \theta)$とすると、$L(\theta; x)$を最大にするような推定量$\theta = \hat{\theta}$を **$\theta$の最尤推定量** という

```{note}
**尤度関数とは**
- サンプルデータが出る確率
- $L(\theta, x)=\prod_{i=1}^n f(x_i|\theta)$

**対数尤度関数とは**
- 微分が楽になるので、尤度関数を対数変換したもの
- $\sum_{i=1}^n f(x_i|\theta)$
```

## 最小二乗法(OLS)

簡単に言うと
: サンプルデータとの誤差が最小になる物を探す
概要
: 誤差を伴う測定値の処理において、その誤差の二乗の和を最小にすることで、最も確からしい関係式を求める方法

数式で表現
: $\sum^n_{i=1} {y_i - f(x)}^2$が最小になる$f(x)$を求める事

前提
: 測定データ$y$はモデル関数$f(x)$と誤差$\epsilon$を使い
$ y = f(x) + \epsilon $
と表せるとする。この時、誤差$\epsilon$は、
- 平均値 = 0 (偏りがない)
- 共分散 $V[\epsilon] = 0$ (各測定は独立)
- 正規分布


### 線形回帰
$x, y$の関係が、次の式で近似出来ているとする。

$$
y_i = \sum^k_{j=1} x_{ij} \beta_j + \beta_0 + \epsilon_i
$$

この時、yの残差

$$ y_i - (\sum_{j=1}^K x_{ij} \beta_j + \beta_0)$$

の二乗和

$$ \sum_{i=0}^n (y_i - (\sum_{j=1}^K x_{ij} \beta_j + \beta_0))^2 $$

を最小にする$\beta$を求める事を最小二乗法と言う

### 最尤推定との関係

誤差$\epsilon$を考えると、

$$
y_i = \hat{y}_i + \epsilon_i\\
= \sum^k_{j=1} x_{ij} \beta_j + \beta_0 + \epsilon_i\\
より、\\
\epsilon = y_i - (\sum^k_{j=1} x_{ij} \beta_j + \beta_0)
$$

誤差項が正規分布に従うとすると、その確率分布は正規分布の確率分布

$$f(x; \mu, \sigma^2)=\dfrac{1}{\sqrt{2 \pi \sigma ^2}}
exp
[-\dfrac{(x-\mu)^2}{2\sigma ^2}
]$$

になる。

正規分布に従う誤差が同時に観測される確率$L$は対数尤度の式より、

$$
L(x)
&= \prod_{i=1}^n f(x_i)\\
&= \prod_{i=1}^n
\dfrac{1}{\sqrt{2 \pi \sigma ^2}}
exp
[-\dfrac{(x-\mu)^2}{2\sigma ^2}]
$$

その対数尤度関数は、

$$
L(x) &= \sum_{i=1}^n ln \dfrac{1}{\sqrt{2 \pi \sigma^2}}
exp
[-\dfrac{(x-\mu)^2}{2\sigma ^2}
]\\

&=\sum_{i=1}^n
\ln \dfrac{1}{\sqrt{2 \pi \sigma^2}}
+ \sum_{i=1}^n
\ln exp[-\dfrac{(x-\mu)^2}{2\sigma ^2}
]\\

&=\sum_{i=1}^n
(\ln 1 - \ln \sqrt{2 \pi \sigma^2})
+ \sum_{i=1}^n
-\dfrac{1}{2\sigma ^2}(x-\mu)^2\\

&=\sum_{i=1}^n
(0 - \ln (2 \pi \sigma^2)^{\dfrac{1}{2}})
-\dfrac{1}{2\sigma ^2}
 \sum_{i=1}^n
(x-\mu)^2\\

&= - \dfrac{n}{2} \ln (2 \pi \sigma^2)
-\dfrac{1}{2\sigma ^2}
 \sum_{i=1}^n
(x-\mu)^2\\

&=- \dfrac{n}{2} \ln (2 \pi \sigma^2)
-\dfrac{1}{2 \sigma^2}
\sum_{i=1}^n
(y_i - (\sum_{j=1}^k x_{ij} \beta_j + \beta_0))^2
$$

ここで$\dfrac{n}{2} \ln (2 \pi \sigma^2)$は$\beta$に対して定数項なので、上記の対数尤度関数を最大化する$\beta$を求めることは

$$ \sum_{i=1}^n
(y_i - (\sum_{j=1}^k x_{ij} \beta_j + \beta_0))^2
$$

を最小化する事と等しい

