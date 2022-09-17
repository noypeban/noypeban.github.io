# 情報理論

## 自己情報量

自己情報量 (選択情報量, 自己エントロピー)
: ある事象の起こりにくさを数値化した物

$$
自己情報量 I(x) = - \log_2 P(x)
$$

情報量の加法性
: 独立な事象A, Bが独立に起きるとき、事象「AもBも起きる」の情報量はAとBの情報量の和になる

$$
I(A, B) = -\log(A, B)\\
= -\log P(A) \cdot P(B)\\
= - [\log P(A) + \log P(B)]\\
= I(A) + I(B)
$$

## 平均情報量

平均情報量 (平均情報量、シャノン情報量、情報論のエントロピー)
: 情報量の期待値

$$
平均情報量 H = -\sum P(E) \log P(E)
$$

### 例題

Q. こんなサイコロの情報量は？

| 確率変数X | 1 | 2 | 3 | 4 | 5 | 6 |
| --- | --- | --- | --- | --- | --- | --- |
| 確率P | 0.5 | 0.1 | 0.1 | 0.1 | 0.1 | 0.1 |

４が出た時の自己情報量：$- \log_2 \dfrac{1}{10} = \log_2 10$

平均情報量：$H=-(0.5 \times \log_2 0.5 + 0.1 \times \log_2 0.1 \times 5) = -0.5\log_20.5-0.5\log_2 0.1$

## 交差エントロピー

２つの確率分布がまったく同じ時に最小となる
分類問題の損失関数で用いられる。

## 結合エントロピー

離散型：$H(X,Y)=-\sum_{i=1}^{M_X}
\sum_{j=1}^{M_Y}
P(x_i, y_j) \log P(x_i, y_j)$

連続型：$H(X,Y) = \int P(x_i, y_j) \log P(x_i, y_j) \ dxdy$

## KLダイバージェンス

KLダイバージェンス（カルバック・ライブラーダイバージェンス）
: ２つの確率分布の近さを表現する量

$$
D_{KL}(p||q)=\sum_x p(x) \log \dfrac{p(x)}{q(x)}
$$

## 相互情報量

２つの情報が得られた事により、どれくらい不確実性が減ったかを示す量

$$
I(X, Y) = H(X)-H(X|Y)\\
= H(Y) - H(Y|X)\\
= H(X) + H(Y) - H(X, Y)
$$

- $I(X, Y)$: XとYの相互情報量
- $H(X)$: Xの自己エントロピー
- $H(Y)$: Yの自己エントロピー
- $H(X|Y)$: $Y$がわかった上での$X$の条件付きエントロピ
- $H(X, Y)$: $X, Y$の結合エントロピー

## 条件付きエントロピー


**Yに対するXの条件付きエントロピー**

$$
H(X|Y) = - \sum_y p(y) \sum_x p(x|y) \log P(x|y)\\
= - \sum_x \sum_y p(x, y) \log P(x|y)\\
= -\sum_y P(y) H(X|Y=y)
$$

**$Y=y$が与えられているときの条件付きエントロピー**

$$
H(X|Y=y) = - \sum_x^X P(x|y) \log P(x|y)
$$

### 例題：野球の結果と機嫌

> カープの勝敗を伝える情報源$A$があったとします。
100日間のカープの勝敗を記録した結果、60日は勝利、40日は負けていました。
また、カープファンであるMくんのカープの試合があった翌日の機嫌を100日間集計した結果、機嫌がよい日が55日、機嫌が悪い日が45日ありました。
https://www.momoyama-usagi.com/entry/info-entropy#2-3

１００日間の集計結果はこうなっていたとする。

B\A|win|lose|計
-|-|-|-
good|40|15|55
bad|20|25|45
計|60|40|100

ここから、「Mくんの機嫌がわかった場合の、カープの勝敗を表す条件付きエントロピー$H(A|B)$」を次の式

$$
H(A|B) = -\sum_b^B P(b) \sum_a^A p(a|b) \log p(a|b)
$$

を使って求めてみる。

$B$|$P(b)$|$P(A_{win} \mid b)$|$P(A_{lose} \mid b)$
-|-|-|-
good|$\dfrac{55}{100}$|$\dfrac{40}{55}$|$\dfrac{15}{55}$
bad|$\dfrac{45}{100}$|$\dfrac{20}{45}$|$\dfrac{25}{45}$

$$
H(A|B) = - \dfrac{55}{100} \left(
    \dfrac{40}{55} \log \dfrac{40}{55} + 
    \dfrac{15}{55} \log \dfrac{15}{55}
\right)
- \dfrac{45}{100} \left(
    \dfrac{20}{45} \log \dfrac{20}{45} + 
    \dfrac{25}{45} \log \dfrac{25}{45}
\right)

$$

### 例題：天気

> 東京の天気の確率$X$が晴れ1/2、曇り1/4、雨1/4とする。気温が25度以上になる確率$Y$が、晴れの場合3/4、曇りの場合1/2、雨の場合1/4だったとする。条件付きエントロピー$H(X|Y), H(Y|X)$を求めよ。
> https://detail.chiebukuro.yahoo.co.jp/qa/question_detail/q10174127805

$H(Y|X)$を求める

X|$P(x)$|$P(y_{25度以上} \mid x)$|$P(y_{25度未満} \mid x)$
-|-|-|-
晴れ|$\dfrac{1}{2}$|$\dfrac{3}{4}$|$\dfrac{1}{4}$
曇り|$\dfrac{1}{4}$|$\dfrac{1}{2}$|$\dfrac{1}{2}$
雨　|$\dfrac{1}{4}$|$\dfrac{1}{4}$|$\dfrac{3}{4}$

$$
H(Y|X) = - \dfrac{1}{2} \left(
    \dfrac{3}{4} \log \dfrac{3}{4} + 
    \dfrac{1}{4} \log \dfrac{1}{4}
\right) - \dfrac{1}{4} \left(
    \dfrac{1}{2} \log \dfrac{1}{2} +
    \dfrac{1}{2} \log \dfrac{1}{2}
\right) - \dfrac{1}{4} \left(
    \dfrac{1}{4} \log \dfrac{1}{4} +
    \dfrac{3}{4} \log \dfrac{3}{4}
\right)\\

= - \dfrac{1}{2} \left(
    \dfrac{3}{4} \left( \log 3 - \log_2 4 \right)
    - \dfrac{1}{4} \log_2 4
\right) - \dfrac{1}{4} \left(
    - \dfrac{1}{2} 
    - \dfrac{1}{2}
\right) - \dfrac{1}{4} \left(
    - \dfrac{1}{4} \times 2 +
    \dfrac{3}{4} \left(\log 3 - 2 \right)
\right)\\

= - \dfrac{1}{2} \left(
    \dfrac{3}{4} \log 3
    - \dfrac{3}{4} \cdot 2 
    - \dfrac{1}{4} \cdot 2
\right) - \dfrac{1}{4} \left(
    - 1
\right) - \dfrac{1}{4} \left(
    - \dfrac{1}{2}
    + \dfrac{3}{4} \log 3
    - \dfrac{3}{2}
\right)\\

= - \dfrac{1}{2} \left(
    \dfrac{3}{4} \log 3
    -2
\right) + \dfrac{1}{4} 
- \dfrac{1}{4} \left(
    - \dfrac{4}{2}
    + \dfrac{3}{4} \log 3
\right)\\

= -\dfrac{3}{8} \log 3
+ 1
+ \dfrac{1}{4} 
+ \dfrac{1}{2}
- \dfrac{3}{16} \log 3\\

= - \dfrac{9}{16} \log 3 - \dfrac{7}{4}
$$

#### $H(X|Y)$を求める

問題文に$P(Y|X)$はあるが$P(X|Y)$がないので求めていく。まず、$P(X \cap Y)$を求めて表にする。

$$
P(X \cap Y) = P(X) \times P(Y|X)\\
より\\

P(25度以上 \cap 晴れ) = P(X_{晴れ})\times P(X_{晴れ}|Y_{25度以上})\\
\dfrac{1}{2} \times \dfrac{3}{4}=\dfrac{3}{8}
$$

よって、$P(X \cap Y)$の表を埋めると、

天気\気温|25度以上|未満|計
-|-|-|-
晴れ|$\dfrac{3}{8}$|$\dfrac{1}{8}$|$\dfrac{1}{2}$
曇り|$\dfrac{1}{8}$|$\dfrac{1}{8}$|$\dfrac{3}{8}$
雨|$\dfrac{1}{16}$|$\dfrac{3}{16}$|$\dfrac{1}{4}$
計|$\dfrac{9}{16}$|$\dfrac{7}{16}$|$1$

ここから、$P(X|Y)=P(X \cap Y) \div P(Y)$を使って$P(x|y)$の表を作ると

$Y$|$P(y)$|$P(晴れ \mid y)$|$P(曇り \mid y)$|$P(雨 \mid y)$
-|-|-|-|-
25℃以上|$\dfrac{9}{16}$|$\dfrac{3}{8}\div\dfrac{9}{16}=\dfrac{2}{3}$|$\dfrac{1}{8}\div\dfrac{9}{16}=\dfrac{2}{9}$|$\dfrac{1}{16}\div\dfrac{9}{16}=\dfrac{1}{9}$
25℃未満|$\dfrac{7}{16}$|$\dfrac{1}{8}\div\dfrac{7}{16}=\dfrac{2}{7}$|$\dfrac{1}{8}\div\dfrac{7}{16}=\dfrac{2}{7}$|$\dfrac{3}{16}\div\dfrac{7}{16}=\dfrac{3}{7}$

$$
H(X|Y) = - \dfrac{9}{16} \left(
    \dfrac{2}{3} \log \dfrac{2}{3}
    + \dfrac{2}{9} \log \dfrac{2}{9}
    + \dfrac{1}{9} \log \dfrac{1}{9}
\right)
- \dfrac{7}{16} \left(
    \dfrac{2}{7} \log \dfrac{2}{7}
    + \dfrac{2}{7} \log \dfrac{2}{7}
    + \dfrac{3}{7} \log \dfrac{3}{7}
\right)\\

 = - \dfrac{9}{16} \left(
    \dfrac{2}{3} (1- \log 3)
    + \dfrac{2}{9} (1-\log 3^2)
    - \dfrac{1}{9} \log 3^2
\right)
- \dfrac{7}{16} \left(
    \dfrac{4}{7} (1 - \log 7)
    + \dfrac{3}{7} (\log 3 - \log 7)
\right)\\

 = - \dfrac{9}{16} \left(
    \dfrac{2}{3} - \dfrac{2}{3}\log 3
    + \dfrac{2}{9} - \dfrac{4}{9} \log 3
    - \dfrac{2}{9} \log 3
\right)
- \dfrac{7}{16} \left(
    \dfrac{4}{7} - \dfrac{4}{7} \log 7
    + \dfrac{3}{7} \log 3 - \dfrac{3}{7} \log 7
\right)\\

 = - \dfrac{9}{16} \left(
    (- \dfrac{6}{9} - \dfrac{4}{9} - \dfrac{2}{9}) \log 3 
    + \dfrac{6}{9}    
    + \dfrac{2}{9}
\right)
- \dfrac{7}{16} \left(
    \dfrac{4}{7} 
    - \log 7 
    + \dfrac{3}{7} \log 3
\right)\\

 = - \dfrac{9}{16} \left(
    - \dfrac{12}{9}\log 3
    + \dfrac{8}{9} 
\right)
- \dfrac{7}{16} \left(
    \dfrac{4}{7} 
    - \log 7 
    + \dfrac{3}{7} \log 3
\right)\\

 =  \dfrac{12}{16}\log 3
    - \dfrac{1}{2} 
    - \dfrac{1}{4} 
    + \dfrac{7}{16}\log 7 
    - \dfrac{3}{16} \log 3
\\

 =  (\dfrac{12}{16}- \dfrac{3}{16})\log 3
    + \dfrac{7}{16}\log 7 
    - \dfrac{2}{4} 
    - \dfrac{1}{4} 
\\

 =  \dfrac{9}{16} \log 3
    + \dfrac{7}{16} \log 7 
    - \dfrac{3}{4} 
\\


$$

### 例題：サイコロ

> - 事象A:サイコロを振って出た目
> - 事象B(b1,b2)
>   - b1:サイコロの目は3の倍数
>   - b2:サイコロの目は3の倍数以外
> 
>サイコロは普通のサイコロです。(1から6全て確率1/6)。
>この時、サイコロの目が事前に3の倍数だと分かっている時の、AのエントロピーH(A|b1)を求めよ
> -- https://okwave.jp/qa/q8213934.html


条件$b1=$「サイコロの目は３の倍数」が分かっているときなので、出目は3か6の２通り。

それぞれの出る確率$P(a|b1)=\dfrac{1}{6}$なので、

$$
H(A|B=b1) = -\sum_a^A P(a|b1) \log P(a|b1)\\
= - 2 \times \dfrac{1}{6} \log \dfrac{1}{6}\\
= \dfrac{1}{3} \log 6\\
= \log 6
$$

### 例題：トランプ

> ジョーカーを除いた52枚のトランプから1枚カードを引くという確率事象系
A
を考える。
>
> (1)　事前に「次のカードはスペードである」と知っているときに得られる平均情報量$H(A|スペード)$を求めなさい。
>
> (2)　事前に「次のカードはキングである」と知っているときに得られる平均情報量$H(A|キング)$を求めなさい。
> -- [「なんとなくわかる」大学の数学・物理・情報](https://www.krrk0.com/conditional-entropy/)

$$
(1) 出るカードはスペードの1からKまでの１３パターンなので、\\
H(A|スペード) = -\sum_{a=1}^{A \in (1,13)}
p(a|スペード) \log p(a|スペード)
\\
= - \dfrac{1}{13} \log \dfrac{1}{13} \times 13\\
= \log 13\\
\\
(2) 出るカードはハート、クラブ、スペード、ダイヤのキング、４パターンなので、\\
H(A|キング) = - 4 \times \dfrac{1}{4} \log \dfrac{1}{4}\\
= - \log 2^{-2}\\
= 2
$$
