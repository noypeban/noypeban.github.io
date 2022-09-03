# Latexの覚書

機械学習の勉強をする際に何度も引いた`Latex`を使った数式の書き方メモ

## 基本演算・記号

演算|latex|結果
-|-|-
乗算|`6 \times 7 = 42`|$6 \times 7 =42$
除算| `42 \div 7 = 6`|$42 \div 7 = 6$
分数|`\frac{1}{2}`|$\frac{1}{2}$
分数（大き目）|`\dfrac{1}{2}`|$\dfrac{1}{2}$
偏微分|`\partial`|$\partial$	
ナブラ|`\nabla`|$\nabla$
内積|`\cdot`|$\cdot$
ルート|`\sqrt{2}`|$\sqrt{2}$
約|`\fallingdotseq`|$\fallingdotseq$


## 数
記号|意味|語源|意味|latex
-|-|-|-|-
$\mathbb{N}$|自然数|Natural Number|正の整数|`\mathbb{N}`
$\mathbb{Z}$|整数|Zehlen(ドイツ語)|自然数＋０＋マイナスの自然数|`\mathbb{Z}`
$\mathbb{Q}$|有理数|Quotient|分数で表せる数|`\mathbb{Q}`
$\mathbb{R}-\mathbb{Q}$|無理数||循環しない無限に続く少数|
$\mathbb{R}$|実数|Real Number|有理数と無理数をあわせたもの|`\mathbb{R}`

## 行列
```latex
\begin{pmatrix}
a & b\\
c & d
\end{pmatrix}
```

$$
\begin{pmatrix}
a & b\\
c & d
\end{pmatrix}
$$

## 集合
```latex
a \in S # 要素aは集合Sの一部
S \ni a
b \notin S
S \notni b
M \subset S　#集合Mは集合Sの一部
S \supset M
N \not\subset S
S \not\supset N

a \cup b # aとbの和集合
a \cap b # aとbの共通部分
```

$$
a \in S\\
S \ni a\\
b \not\in S\\
S \not\ni b\\
M \subset S\\
S \supset M\\
N \not\subset S\\
S \not\supset N\\
\\
a \cup b\\
a \cap b
$$

