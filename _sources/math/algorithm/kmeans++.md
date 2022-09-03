# k-means++

- k-meansの初期値依存問題を解決するために考えられた手法。
- 中心点の座標をランダムに選択する所が違う

## アルゴリズム

1. ランダムに１つのデータ点をクラスタ中心として選択する
2. 次のクラスタ中心は、１から遠いデータ点が選択されるように以下の式で選ぶ

	$$あるデータ点が選択される重み付き確率分布=\dfrac{D(x)^2}{\sum D(x)^2}\\
	D(x)はデータ点１からxまでの距離$$

3. ２を繰り返してk個のクラスタ中心を選ぶ
4. 普通のk-means法でクラスタリングする

## 実装

```python
import numpy as np

k=4

# 200個のデータ点を用意
n=200
data = np.random.randn(n, 2)

# == クラスタ中心を決める処理 ==
# データ点がクラスタ中心として選択される確率を保存する入れ物。最初の確率は均等
probabilities = np.repeat(1/n, n) #=>(200, )
# クラスタの中心点座標を保存する入れ物
centroids = np.zeros((k, 2)) #=>(4, 2)
# 距離を保存する入れ物
distances = np.zeros((n, k)) #=>(200, 4)

for i in range(k):
  # probabilitiesの確率に従ってセントロイドとなる点をdataから選択する
  centroids[i] = data[np.random.choice(np.arange(n), p=probabilities, size=(1))]
  # dataとcentroidsの距離の二乗をとる
  distances[:, i] = np.sum((data - centroids[i])**2, axis=1)
  # probabilitiesを更新する
  probabilities = np.sum(distances, axis=1)/np.sum(distances)
  # np.sum(distances, axis=1)=>(200,) np.sum(distances)=>float
```

