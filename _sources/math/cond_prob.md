# 条件付き確率

## 定義

条件付き確率
: 「事象 $A$ が起きた」と分かったもとでの事象 $B$ が起こる確率

$$
P(B|A) = \dfrac{P(A \cap B)}{P(A)}\\
P(A|B) = \dfrac{P(A \cap B)}{P(B)}
$$

変形すると、

$$
P(A\cap B)=\\
P(A)\times P(B|A) = P(B) \times P(A|B)
$$

事象の数をベースに、このように表現することもできる

$$
P(B|A) = \dfrac{|A\cap B|}{|A|}
$$

## 例題

### サイコロ
> サイコロを1つ振った。出目を見逃してしまったが，友人が出目は偶数だと教えてくれた。このとき出目が 4 以上であった確率を求めよ。
> --[高校数学の美しい物語](https://manabitimes.jp/math/1061)

- 事象A: 4以上が出た
- 事象B: 偶数が出た
- 求める確率: $P(A|B) = \dfrac{P(A\cap B)}{P(B)}$

$$
P(B) = (偶数が出る確率)\\
\dfrac{3}{6}\\
P(A\cap B) = (4以上の偶数が出る確率)\\
= \dfrac{2}{6}\\
P(A|B) = (偶数が出た上で4以上が出る確率）\\
= \dfrac{P(A\cap B)}{P(A)}\\
=\dfrac{\dfrac{2}{6}}{\dfrac{3}{6}}
=\dfrac{2}{3}
$$

事象の数ベースで考えても、

$$
P(A|B) = \dfrac{|A\cap B|}{|A|}\\
=\dfrac{2}{3}
$$

### 男の子、女の子
> ある夫婦には子供が二人いる。二人のうち少なくとも一人は男の子ということが分かった。このとき，二人とも男の子である確率を求めよ。ただし，男の子が生まれる確率，女の子が生まれる確率はともに $\dfrac{1}{2}$ とする
> --[高校数学の美しい物語](https://manabitimes.jp/math/1061)

- 事象A: 二人とも男の子
- 事象B: 一人が男の子
- 求める確率: $P(A|B) = \dfrac{P(A\cap B)}{P(B)}$

- 子供の組み合わせ: 男男,男女,女男,女女


$$
P(B) = (一人が男の子の確率)\\
= \dfrac{3}{4}\\
P(A\cap B) = (一人が男の子かつ二人が男の子の確率)\\
= \dfrac{1}{4}\\
P(A|B) = \dfrac{P(A\cap B)}{P(B)}\\
= \dfrac{\dfrac{1}{4}}{\dfrac{3}{4}}\\
=\dfrac{1}{3}
$$

### 検査と感染
> とある病気にかかっているか判定する検査について考える。この病気は 10 万人に一人が罹患している。「病気なのに陰性と判定してしまう確率」「病気でないのに陽性と判定してしまう確率」はともに 0.01 であるとする。太郎さんが陽性と判定されたとき，本当に病気にかかっている確率を求めよ。
> --[高校数学の美しい物語](https://manabitimes.jp/math/1061)

- 事象A: 感染している
- 事象B: 検査で陽性
- 求める確率: $P(A|B) = \dfrac{P(A\cap B)}{P(B)}$

-|感染|してない
-|-|-
陽性|0.99|0.01
陰性|0.01|0.99

$$
P(B|A) = (感染した上で陽性の確率)\\
= 0.99\\

P(B) = (検査で陽性の確率)\\
= (感染かつ陽性) + (非感染かつ陽性)\\
= 0.00001 * 0.99 + 0.99999 * 0.01\\
=0.0000099+0.0099999\\
=0.0100098\\
P(A\cap B) = P(A)\times P(B|A)\\
=0.00001 \times 0.99\\
=0.0000099\\
P(A|B) = \dfrac{P(A\cap B)}{P(B)}\\
=0.0000099 \div 0.0100098\\
= 9.890307498651322e-4\\
\fallingdotseq 0.001
$$

### １と書かれた赤玉

> 次の図の袋の中には、赤い玉が3つ、白い玉が3つ入っています。赤い玉のうち2つには「1」、残りの1つには「2」と書かれています。一方、白い玉のうち2つには「2」、残りの1つには「1」と書かれています。この袋の中から玉を1つ取り出す時、「1」と書かれた赤色の玉が取り出される確率はいくらでしょうか。
> -- [統計web](https://bellcurve.jp/statistics/course/6438.html)

- 事象A: １と書かれている
- 事象B: 赤玉
- 求める確率: $P(A\cap B)$

$$ P(A \cap B) = \dfrac{2}{6} = \dfrac{1}{3}$$

> 例題1と同じ袋の中から玉を1つ取り出した時、その玉は赤色でした。この赤い玉に「1」と書かれている確率はいくらでしょうか。
> -- [統計web](https://bellcurve.jp/statistics/course/6438.html)

- 事象A: １と書かれている
- 事象B: 赤玉
- 求める確率: $P(A|B) = \dfrac{P(A\cap B)}{P(B)}$

$$
P(B) = \dfrac{3}{6}\\
P(A \cap B) = \dfrac{2}{6}\\
\therefore P(A|B) = \dfrac{P(A \cap B)}{P(B)}\\
= \dfrac{2}{3}
$$

### サイコロの出目の和

> さいころを2回投げて出た目の和が8以上となる確率はいくらでしょうか。ただし、1回目に出た目は「4」であることが分かっています
> -- [統計web](https://bellcurve.jp/statistics/course/6438.html)

- 事象A: 和が8以上
- 事象B: 4が出る
- 求める確率: $P(A|B)=\dfrac{P(A\cap B)}{P(B)}$

$$
P(B) = P(4が出る確率)\\
= \dfrac{1}{6}\\
P(A \cap B) = P(4が出てかつ、2回目に4以上が出る確率)\\
= \dfrac{1}{6} \times \dfrac{3}{6}\\
\therefore P(A|B) = \dfrac{P(A \cap B)}{P(B)}\\
= \dfrac{\dfrac{1}{6}\times \dfrac{3}{6}}{\dfrac{1}{6}}\\
= \dfrac{3}{6} = \dfrac{1}{2}
$$

### カード戻さず
> 1 から 13 までの番号が書いてあるカードが 13 枚
入っている箱から，カードを 1 枚取り出し，それ
を戻さずに，続けてもう 1 枚取り出します。1 回目
に偶数が出たとき， 2 回目は奇数がでる確率を求
めなよ。
> -- [iドリル](https://iidrill.com/material/4%E8%AC%9B%E3%80%80%E6%9D%A1%E4%BB%B6%E4%BB%98%E3%81%8D%E7%A2%BA%E7%8E%87%EF%BC%882%E7%AF%80%E3%80%80%E7%A2%BA%E7%8E%87%EF%BC%89%E3%80%80%E5%95%8F%E9%A1%8C%E9%9B%86%E3%80%90%E9%AB%98%E6%A0%A1%E6%95%B0/)

- 条件A: 1回目に偶数が出る
- 条件B: 2回目に奇数が出る
- 求める確率: $P(B|A)=\dfrac{P(A \cap B)}{P(A)}$

$$
P(A) = \dfrac{6}{13}\\
P(A \cap B) = P(A) \times \dfrac{7}{12}\\
P(B|A) = \dfrac{P(A) \times \dfrac{7}{12}}{P(A)}\\
= \dfrac{7}{12}
$$

### 玉戻さず
> 赤玉 5 個と白玉 3 個の入った袋から，玉を 1 個ずつ
2 個取り出す。ただし，取り出した玉はもとにもどさ
ない。1 個目に赤玉が出たときに，2 個目も赤玉が出
る確率を求めよ。
> -- [iドリル](https://iidrill.com/material/4%E8%AC%9B%E3%80%80%E6%9D%A1%E4%BB%B6%E4%BB%98%E3%81%8D%E7%A2%BA%E7%8E%87%EF%BC%882%E7%AF%80%E3%80%80%E7%A2%BA%E7%8E%87%EF%BC%89%E3%80%80%E5%95%8F%E9%A1%8C%E9%9B%86%E3%80%90%E9%AB%98%E6%A0%A1%E6%95%B0/)

- 事象A: 1回目に赤玉がでる
- 事象B: 2回目に赤玉がでる
- 求める確率: $P(B|A) = \dfrac{P(A \cap B)}{P(A)}$

$$
P(A) = \dfrac{5}{8}\\
P(A \cap B) = P(A) \times \dfrac{4}{7}\\
P(B|A) = \dfrac{4}{7}
$$

### 2回のサイコロの出目の差
> 1つのサイコロを続けて2回振ったときに，1回目の出る目をa，2回目に出る目をbとする．
>
> (i). 事象$|a-b|<5$の起こる確率は？
>
> (ii). 事象$a < 5$が起こった時に、事象$|a-b|<5$の起こる確率は？
> https://www.geisya.or.jp/~mwm48961/koukou/cond_prob.htm

(i) 事象$|a-b| \geq 5$となるケースを数え上げると、

1回目|2回目|abs(a-b)
-|-|-
1|6|5
6|1|5

の2通り。

全事象$U$は$6\times 6=36$通りなので、
事象$|a-b|<5$の起こる確率は

$$
P = \dfrac{36-2}{36} = \dfrac{34}{36}\\
\dfrac{17}{18}
$$

(ii)
- 事象A: $a<5$
- 事象B: $|a-b|<5$
- 求める確率: $P(B|A) = \dfrac{P(A \cap B)}{P(A)}$

$$
P(A) = \dfrac{4}{6}\\
P(A \cap B) = P(aが5未満、かつbとaの差が5未満)\\
$$

事象Bのうち、a>=5のケースは

1回目|2回目|計(通り)
-|-|-
5|1~6|6
6|2~6|5

なので

$$
P(A \cap B) = \dfrac{34-11}{36}=\dfrac{23}{36}\\

\therefore P(B|A) = \dfrac{P(A \cap B)}{P(A)}\\
= \dfrac{\dfrac{23}{36}}{\dfrac{4}{6}}\\
= \dfrac{23}{36} \times \dfrac{6}{4}\\
= \dfrac{23}{6} \times \dfrac{1}{4}\\
= \dfrac{23}{24}
$$

### 2018センター試験 - 大小のサイコロ

> 大小のサイコロを同時に投げる試行において、
> - 事象A: 大きいサイコロで4が出る
> - 事象B: 2個のサイコロの出目の和が7
> - 事象C: 2個のサイコロの出目の和が9
> 1. A,B,Cの確率は？
> 2. それぞれの確率は？
> 	- Cが起きた時のAが起こる条件付確率と、
> 	- Aが起きた時のCが起こる条件付き確率は？
> 3. 不等号は？
> 	- $P(A \cap B)$ vs $P(A)P(B)$
> 	- $P(A \cap C)$ vs $P(A)P(C)$
> 4. 大小2個のサイコロを同時に投げる試行を2回繰り返す。
> 	- 1回目に事象$A\cap B$が起こり、2回目に$\overline{A} \cap C$が起こる確率
> 	- 3つの事象$A, B, C$がそれぞれちょうど1回ずつ起こる確率
> -- [東進](https://www.toshin.com/center/2018/sugaku-1a_mondai_3.html)

1. 事象$A$においては大小のサイコロは独立事象なので、

	$$
	P(A) = \dfrac{1}{6}
	$$

	事象$B$のケースは{1,6},{2,5},{3,4},{4,3},{5,2},{6,1}の6通り。全事象は36通りなので、

	$$
	P(B) = \dfrac{|B|}{|U|} = \dfrac{1}{6}
	$$

	事象$C$のケースは{3,6},{4,5},{5,4},{6,3}の4通りなので、

	$$
	P(C) = \dfrac{|C|}{|U|} = \dfrac{4}{36}
	= \dfrac{1}{9}
	$$

2. $P(A|C)$と$P(C|A)$を求める。事象$A \cap C$は{4, 5}の1通りしかない。

	$$
	P(A) = \dfrac{1}{6}\\
	P(C) = \dfrac{1}{9}\\
	P(A \cap C) = \dfrac{1}{36}\\

	P(A|C) = \dfrac{P(A \cap C)}{P(C)}\\
	= \dfrac{1}{36} \times \dfrac{9}{1}\\
	= \dfrac{1}{4}\\

	P(C|A) = \dfrac{P(A \cap C)}{P(A)}\\
	= \dfrac{1}{36} \times \dfrac{6}{1}\\
	= \dfrac{1}{6}
	$$

3. 事象$A \cap B$は{4, 3}の1通りなので、

	$$
	P(A \cap B) = \dfrac{1}{36}\\
	P(A)P(B) = \dfrac{1}{6} \cdot \dfrac{1}{6}\\
	\dfrac{1}{36} == \dfrac{1}{36}\\
	\therefore
	P(A \cap B) == P(A)P(B)
	$$

	$P(A \cap C)$は問２で求めたので、

	$$
	P(A \cap C) = \dfrac{1}{4}\\
	P(A)P(C) = \dfrac{1}{6} \cdot \dfrac{1}{9}\\
	= \dfrac{1}{54}\\
	\dfrac{1}{4} > \dfrac{1}{54}\\
	\therefore
	P(A \cap C) > P(A)P(C)
	$$

4. 1回目に事象$A\cap B$が起こり、2回目に$\overline{A} \cap C$が起こる確率は、1回目が2回目に影響を与えない独立事象なので、それぞれの確率を掛け算すればよい。

	事象$\overline{A} \cap C$は「大きいサイコロで4以外が出る」かつ「2個のサイコロの出目の合計が９」になる。

	ケースとしては、
	- {3, 6}
	- {5, 4}
	- {6, 3}
	の3通り

	$$
	P(\overline{A} \cap C) = \dfrac{3}{36}\\
	P = P(A \cap B) \cdot P(\overline{A} \cap C)\\
	= \dfrac{1}{36} \cdot \dfrac{3}{36}\\
	= \dfrac{1}{432}
	$$

	事象$A, B, C$がそれぞれ1回ずつ起こる確率は、

	1回目|2回目
	-|-
	$A \cap B$|$\overline{A} \cap C$
	$A \cap C$|$\overline{A} \cap B$
	$\overline{A} \cap B$|$A \cap C$
	$\overline{A} \cap C$|$A \cap B$

	の4パターン考えられる。

	$$
	P(A \cap B) = \dfrac{1}{36}\\
	P(A \cap C) = \dfrac{1}{36}\\
	P(\overline{A} \cap C) = \dfrac{1}{12}\\
	$$

	$\overline{A} \cap B$のケースは、

	- {1, 6}
	- {2, 5}
	- {3, 4}
	- {5, 2}
	- {6, 1}

	の５通りなので、$P(\overline{A} \cap B) = \dfrac{5}{36}$

	$$
	P = P(A \cap B) \cdot P(\overline{A} \cap C)\\
	+ P(A \cap C) \cdot P(\overline{A} \cap B)\\
	+ P(B) \cdot P(A \cap C)\\
	+ P(C) \cdot P(A \cap B)\\
	= 2 \times \dfrac{1}{36} \cdot \dfrac{1}{12}\\
	+ 2 \times \dfrac{1}{36} \cdot \dfrac{5}{36}\\
	= \dfrac{1}{18}(\dfrac{3}{36}+\dfrac{5}{36})\\
	= \dfrac{1}{18} \cdot \dfrac{8}{36}\\
	= \dfrac{1}{9} \cdot \dfrac{1}{9}\
	= \dfrac{1}{81}
	$$
